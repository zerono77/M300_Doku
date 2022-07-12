# Einleitung
Unsere Idee ist es, einen Minecraft server im Container aufzusetzen. Dieser soll immer die selbe Map laden, egal wo es gestartet wird. Wir haben uns kurz informiert und wissen, dass es bereits einen container zum installieren gibt davon.

# Inhaltsverszeichnis

## Services
Docker Hub Seite: https://hub.docker.com/r/itzg/minecraft-server

## Umsetzung

mkdir minecraft-data

touch docker-compose.yml

nano docker-compose.yml

### File 

    version: "3"

    services:
    mc:
        image: itzg/minecraft-server
        ports:
        - 25565:25565
        environment:
        EULA: "TRUE"
        tty: true
        stdin_open: true
        restart: unless-stopped
        volumes:
        # attach a directory relative to the directory containing this compose file
        - ./minecraft-data:/data

sudo apt  install docker-compose

yes

docker-compose up -d

## Testing
Testvorgang | Erwartung | Resultat
-------- | -------- | --------
 Der Container wird offline genommen und neu gestartet | Mit dem Docker-Compose Command, soll der Container mit dem Minecraft server Gestartet werden   | Der Minecraft Server startet sofort. 
Nachdem der Server Neu gestartet wurde, wird geschaut, ob die selbe Welt geladen wird (kontrolle mit bauten im Spiel)   | Die selbe welt sollte geladen werden, mit den vorgemachten Bauten.   | Es wird die Selbe Karte geladen. 


## Quellen
https://github.com/itzg/docker-minecraft-server
