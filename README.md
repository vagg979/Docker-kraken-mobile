# Docker Kraken-mobile
La imagen docker cuenta con las características listas para crear y correr las pruebas en kraken-mobile.

_Los paquetes o características instaladas son:_
- S.O. Ubuntu
- Ruby
- Variables de entorno JAVA_HOME y ANDROID_HOME
- Kraken-mobile

## Comenzando 🚀

_Estas instrucciones te permitirán obtener una copia del proyecto en funcionamiento en tu máquina local **(host)** para propósitos de desarrollo y pruebas._

### Pre-requisitos 📋

_En su **(host)**  debe tener instaladas:_

• Variables de entorno JAVA_HOME y ANDROID_HOME.

• Emuladores android y/o dispositivos físicos.

• Configurar un proyecto kraken-mobile de acuerdo a la documentación oficial.**https://github.com/TheSoftwareDesignLab/KrakenMobile**



### Instalación 🔧

_Debes tener la imagen docker, este proyecto y los prerequisitos en tu máquina, debes tener corriendo los siguientes elementos en tu máquina:_

• Dispositivos android conectados o emulados.

## Ejecutando las pruebas ⚙️

_Con un proyecto kraken-mobile previamente configurado_

1. Iniciar la imagen docker, pasandole como parámetros:

**-it** (Inicia el contenedor de forma interactiva).

**-p** (Puertos que se quieren compartir entre el host y el contenedor para conexión de los dispositivos).

**-v* (Carpeta a compartir enter el host y el contenedor docker en la ruta /mnt/) 

**--name** (Nombre de nuestro contenedor una vez inicie)


**docker run --privileged -it -p 5554:5554 -p 5555:5555 -p 5556:5556 -p 5557:5557 -p 5037:5037 -v ruta/carpeta/host:/mnt/ --name kraken kraken-mobile:1.04**

Si tienes problemas con la versión de adb del contenedor con el de el host, debes remplazar la carpeta **platform_tools** en tu host por la contenida en **platform-tools_r29.0.5-windows.zip**

2. Conectar los dispositivos al contenedor.
_En mi caso los dispositivos están en los puertos 5554 y 5556, debo conectarlos a un puerto más arriba cada uno_:

**adb connect host.docker.internal:5555
adb connect host.docker.internal:5557**

_ejecutar **adb devices** para verificar los dispositivos conectados_

![ejecución adb devices](https://github.com/vagg979/Docker-kraken-mobile/blob/master/images/adb_devices.png)
 
 3. Ingresar a la carpeta **mnt** con el comando **cd mnt/** y ejecutar el comando **kraken-mobile setup** para configurar los dispositivos y las aplicaciones que se ejecutarán durante la prueba.
 
 4. Ejecutar el comando **kraken-mobile run xxxxxx.apk --configuration=kraken_mobile_settings.json --properties=kraken_properties.json**  para correr la prueba con las aplicaciones y procesos configurados.
 

### Resultados de las pruebas 🔩

_Los resultados se pueden visualizar en la carpeta **reports**, estos resultados se guardan en carpetas separadas para cada ejecución y se pueden ver abriendo el archivo **index.html** de cada carpeta._


## Autor ✒️

* **Victor Garcia** - *Trabajo Inicial* - [vagg979](https://github.com/vagg979)

