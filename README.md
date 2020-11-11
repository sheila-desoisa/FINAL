# FINAL
De Soisa - Elihaltt - Karner - Moyano
1.	Iniciamos un montaje de una rapsberrypi  (Karner)
2.	Luego sobre esa instalé un contenedor Docker, sobre el mismo el sistema operativo Ubuntu y sobre él el servicio de html, y le dí la persistencia al mismo. (De Soisa)
3.	Luego para que cada uno de los integrantes del grupo pudiera acceder se habilitó el puerto ssh 6583  con acceso desde cualquier lugar a través del comando:
teckarner.doomdns.org -l unsam  (password 12345678)  (Elihallt)
4.	Sobre otro contenedor íbamos a correr el servicio de SQL (Moyano)
Punto 2:
a.	Instalamos  el Docker
$ sudo apt-get install docker
b.	Instalamos el docker-compose
$ sudo apt-get install docker-compose
c.	Ejecutamos el docker
$ docker-compuse up
d.	Controlamos que la imagen esté instalada
$ sudo docker images
e.	Creamos una CARPETA “final” con el comando mkdir
$ mkdir final
f.	Ingresamos dentro de la misma con el comando cd
$ cd final
g.	Creamos 3 archivos vacíos con el comando touch. 
$ touch Dockerfile
$ touch docker-compose.yml
$ touch index.html
h.	Ediamosé el archivo Dockerfile colocando la siguiente receta:
FROM ubuntu:20.04
ENV TZ=America/Argentina/Buenos_Aires
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN rm -rf /var/lib/apt/lists/* && apt-get update && apt-get install -y apache2 && a$
CMD ["apachectl", "-D", "FOREGROUND"]
Explicación: 
Línea 1: ordenamos que bajara la imagen de UBUNTU versión 20.04
Línea 2: ordenamos tomar la hora (Time Zone) de Buenos Aires – Argentina – América
Línea 3: ordenamos que usara siempre la hora del Host como la misma para la máquina virtual
Línea 4: ordenamos que borrara todas las librerías, accesos directos y listas …. Luego que finalizara esta actividad ok, le concatené la orden con el && para que ejecutara un apt-get update, luego una vez finalizado que siguiera con el apt-get install y que continuara con el apache sin necesidad de que yo coloque “YES” (el a$) no recuerdo que era
Línea 5: le ordené al servidor apache que iniciara nuestro sitio html en modo demonio
i.	Editamos el archivo docker-compose.yml colocando la siguiente receta:
Versión: “3”
services:
  web_apache:
    build: .
    ports:
      - 8081:8081
    volumes:
      - ./:/var/www/html
Explicación: 
Línea 1: colocamos el número de la versión.
Línea 2: colocamos el título de lo que necesitaba configurar en éste caso SERVICIO
Línea 3: colocamos dí un Tab y le coloqué de nombre al web server “web apache”
Línea 4: colocamos que construyera esa imagen desde la ubicación donde estuviera parado independientemente de la misma.
Línea 5: colocamos los puertos 8081 de mi HOST con el 8081 de mi contenedor
Línea 6: colocamos el volumen para que quedara persistente que desde la ubicación de mi HOST donde estuviera parado fuera hacia la carpeta /var/www/html del conteiner.
j.	Edité el archivo index.html colocando la siguiente receta:
<html>
        <head>
                <title>Hola Profe enesima prueba de docker con volumen</title>
        </head>
<body>
        <h1>De Soisa - Elihaltt - Karner - Moyano - Gracias por la cursada amigos</h1> </body>
</html>
Explicación: 
Línea 1: ordenamos iniciar la página
Línea 2: un tab y le marqué el inicio del encabezado
Línea 3: otro tab y le marqué el inicio del título, a continuación escribí el título y le maqué la finalización del mismo.
Línea 4: marcar la finalización del encabezado.
Línea 5: marcar el inicio del cuerpo.
Línea 6: marcar el inicio del texto, el texto y la finalización del mismo.
Línea 7: marcar la finalización del cuerpo.
Línea 8: marcar la finalización de la página.

Abrir el explorador de mi MV y coloqué teckarner.doomdns.org:8081 para corroborar la página.

  
 
 


