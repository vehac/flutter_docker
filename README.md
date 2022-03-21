# Flutter
Docker - Flutter - VS Code

Crear un espacio de trabajo (workspace) con docker para poder crear proyectos usando flutter.

El archivo devcontainer.json está configurado para equipos con sistema operativo Linux, en el caso se use en otro sistema operativo retirar lo siguiente:
 
```bash
"source=/dev/bus/usb,target=/dev/bus/usb,type=bind"
```
Como requisito en VS Code se debe instalar: [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker/) y [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack/)

## Docker

- Para iniciar el contenedor, en VS Code seleccionar la siguiente opción:
```bash
Open Folder in Container
```
- Luego abrir el directorio raíz que contiene el Dockerfile.

- Al finalizar la compilación, se abrirá la terminal bash del contenedor.

- Para finalizar el contenedor, en VS Code seleccionar la siguiente opción:
```bash
Close Remote Connection
```
## Crear proyecto con Flutter:
- Para verificar flutter, dentro del contenedor ejecutar:
```bash
flutter doctor
```
- Para crear un proyecto con flutter, hacerlo dentro del contenedor en la carpeta workspace, para ello ejecutar:
 ```bash
flutter create nombre_proyecto
```

### Ver proyecto en web:
- Para generar el proyecto para web, dentro de la carpera nombre_proyecto (nombre de la carpeta del proyecto), ejecutar:
```bash
flutter pub get && flutter run -d web-server --web-port 5000 --web-hostname 0.0.0.0
```

- Para ver el proyecto generado para web, en un navegador colocar la siguiente url:
```bash
http://localhost:5000
```

### Ver proyecto en dispositivo android:
- Habilitar depuración usb, conectar por usb y configurar estableciendo el modo de conexión en PTP en el dispositivo android. Nota: Tener cerrado el navegador chrome en el equipo host, para poder usar el dispositivo android en el contenedor.

- Para verificar que el dispositivo android fue reconocido, ejecutar:
```bash
flutter doctor
```
- Para generar el proyecto para android, dentro de la carpera nombre_proyecto (nombre de la carpeta del proyecto), ejecutar:
```bash
flutter pub get && flutter run
```

## Referencia
[Flutter con Docker](https://blog.codemagic.io/how-to-dockerize-flutter-apps/)