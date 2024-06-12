# orangepi_media_server
Configurações para meu servidor baseado em orangepi

# Jellyfin

### Copiando arquivos de configuração ao diretório correto
```bash
sudo mkdir /var/jellyfin  # cria o diretório base
sudo mkdir /var/jellyfin/config  
sudo mkdir /var/jellyfin/cache  
sudo chown $USER:$USER -R /var/jellyfin # dá a permissão ao seu usuário
```

### Testando se está executando
É o mesmo comando executado ao subir o serviço
```
sudo docker compose -f /var/jellyfin/jellyfin.yml up
```
Observe se não recebe nenhum erro
No comando abaixo eu já havia executado uma vez, então espere que o docker baixe e descompacte a imagem inicial.
```
[+] Running 1/0
 ✔ Container jellyfin  Created                                                                                     0.0s
Attaching to jellyfin
jellyfin  | [02:57:32] [INF] [4] Main: Jellyfin version: 10.9.6
jellyfin  | [02:57:32] [INF] [4] Main: Environment Variables: ["[JELLYFIN_FFMPEG, /usr/lib/jellyfin-ffmpeg/ffmpeg]", "[JELLYFIN_LOG_DIR, /config/log]", "[JELLYFIN_WEB_DIR, /jellyfin/jellyfin-web]", "[JELLYFIN_PublishedServerUrl, http://192.168.0.100]", "[JELLYFIN_CACHE_DIR, /cache]", "[JELLYFIN_DATA_DIR, /config]", "[JELLYFIN_CONFIG_DIR, /config/config]"]
jellyfin  | [02:57:32] [INF] [4] Main: Arguments: ["/jellyfin/jellyfin.dll", "--ffmpeg", "/usr/lib/jellyfin-ffmpeg/ffmpeg"]
jellyfin  | [02:57:32] [INF] [4] Main: Operating system: Debian GNU/Linux 12 (bookworm)
jellyfin  | [02:57:32] [INF] [4] Main: Architecture: Arm64
jellyfin  | [02:57:32] [INF] [4] Main: 64-Bit Process: True
jellyfin  | [02:57:32] [INF] [4] Main: User Interactive: True
jellyfin  | [02:57:32] [INF] [4] Main: Processor count: 4
jellyfin  | [02:57:32] [INF] [4] Main: Program data path: /config
jellyfin  | [02:57:32] [INF] [4] Main: Log directory path: /config/log
jellyfin  | [02:57:32] [INF] [4] Main: Config directory path: /config/config
jellyfin  | [02:57:32] [INF] [4] Main: Cache path: /cache
jellyfin  | [02:57:32] [INF] [4] Main: Web resources path: /jellyfin/jellyfin-web
jellyfin  | [02:57:32] [INF] [4] Main: Application directory: /jellyfin/
jellyfin  | [02:57:32] [INF] [4] Jellyfin.Server.Migrations.MigrationRunner: Marking following migrations as applied because this is a fresh install: ["CreateNetworkConfiguration", "MigrateMusicBrainzTimeout", "MigrateNetworkConfiguration"]
jellyfin  | [02:57:33] [INF] [4] Emby.Server.Implementations.AppBase.BaseConfigurationManager: Setting cache path: /cache
jellyfin  | [02:57:33] [INF] [4] Emby.Server.Implementations.ApplicationHost: Loading assemblies
jellyfin  | [02:57:33] [INF] [4] Jellyfin.Networking.Manager.NetworkManager: Defined LAN subnets: ["127.0.0.1/8", "10.0.0.0/8", "172.16.0.0/12", "192.168.0.0/16"]
jellyfin  | [02:57:33] [INF] [4] Jellyfin.Networking.Manager.NetworkManager: Defined LAN exclusions: []
jellyfin  | [02:57:33] [INF] [4] Jellyfin.Networking.Manager.NetworkManager: Used LAN subnets: ["127.0.0.1/8", "10.0.0.0/8", "172.16.0.0/12", "192.168.0.0/16"]

========================================================================
ApplicationHost: Core startup complete
jellyfin  | [02:57:53] [INF] [4] Main: Startup complete 0:00:21.7055072
jellyfin  | [02:57:54] [INF] [11] Emby.Server.Implementations.ScheduledTasks.TaskManager: Clean up collections and playlists Completed after 0 minute(s) and 0 seconds
jellyfin  | [02:57:59] [INF] [12] Emby.Server.Implementations.ScheduledTasks.TaskManager: Update Plugins Completed after 0 minute(s) and 5 seconds
jellyfin  | [03:00:00] [INF] [23] Emby.Server.Implementations.ScheduledTasks.TaskManager: Generate Trickplay Images Completed after 0 minute(s) and 0 seconds
jellyfin  | [03:00:01] [INF] [19] Emby.Server.Implementations.ScheduledTasks.TaskManager: Daily trigger for Generate Trickplay Images set to fire at 2024-06-13 03:00:00.000 +00:00, which is 23:59:58.9960100 from now.
```
Acesse no navegador o endereço da sua máquina seguido de :8096, exemplo:  
http://192.168.0.2:8096  
Verá uma tela para criar sua conta no serviço do Jellyfin, caso tenha feito isso antes ou tenha uma cópia da pasta "config", poderá entrar em sua conta.  

Recomendo pressionar CTRL+C no terminal atual e subir o serviço em definitivo.  
```
sudo systemctl enable jellyfin
sudo systemctl start jellyfin
```
