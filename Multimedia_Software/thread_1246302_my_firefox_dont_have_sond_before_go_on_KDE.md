---
title: "my firefox dont have sond before go on KDE"
date: 2009-08-21
forum: Multimedia Software
---

### Post by cammell on 2009-08-21
hi i'm seeing between updates so I decided to enter my first kde thing that was installed by the amarok and kaffeine so I saw that I could also configure compiz; but the manager did what he felt like and compiz no way forward, now I'm angry and I close the kde sesion and i return to gnome again but put a video in firefox I can see who has remained silent on youtube, so I'm angry and I realize that this whole compiz misconfigured with few options but without any sent; so more angry em even more and go to konkeror; i put the the same video and same goes silent ... I have (or at least had) all set to ALSA Server, to avoid fights, but as I have read in a British blog then KDE usually kidnap the output of the sound, now I've tried to go to KDE and put back the same video and I cn see than sounds works correctly ... So that's why we walk here and now clarifies all the other audio programs that use alsa or relationship with them working properly (on gnome) .... in fact I've already been 2 weeks with the problem that I have been breaking the skull but as I get tired and find nothing in google I ask for help ...
EDIT-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

I FIXED WITH THIS:
(SORRY BUT IS ONLY AVILABLE IN SPANISH)






cammell@cammell-laptop:~$ sudo apt-get install libflash-mozplugin
[sudo] password for cammell:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
libflash0c2
Se instalarán los siguientes paquetes NUEVOS:
libflash-mozplugin libflash0c2
0 actualizados, 2 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 85.0kB de archivos.
Se utilizarán 365kB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? A
Abortado.
cammell@cammell-laptop:~$ sudo apt-get install libflash-mozplugin
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
libflash0c2
Se instalarán los siguientes paquetes NUEVOS:
libflash-mozplugin libflash0c2
0 actualizados, 2 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 85.0kB de archivos.
Se utilizarán 365kB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? S
Des:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libflash0c2 0.4.13-9ubuntu1 [70.2kB]
Des:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libflash-mozplugin 0.4.13-9ubuntu1 [14.7kB]
Descargados 85.0kB en 1s (76.2kB/s)
Seleccionando el paquete libflash0c2 previamente no seleccionado.
(Leyendo la base de datos ...
344972 ficheros y directorios instalados actualmente.)
Desempaquetando libflash0c2 (de .../libflash0c2_0.4.13-9ubuntu1_i386.deb) ...
Seleccionando el paquete libflash-mozplugin previamente no seleccionado.
Desempaquetando libflash-mozplugin (de .../libflash-mozplugin_0.4.13-9ubuntu1_i386.deb) ...
Configurando libflash0c2 (0.4.13-9ubuntu1) ...

Configurando libflash-mozplugin (0.4.13-9ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
cammell@cammell-laptop:~$ sudo apt-get install libflashsupport
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes NUEVOS:
libflashsupport
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 8326B de archivos.
Se utilizarán 65.5kB de espacio de disco adicional después de desempaquetar.
Des:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libflashsupport 1.9-0ubuntu1 [8326B]
Descargados 8326B en 0s (12.9kB/s)
Seleccionando el paquete libflashsupport previamente no seleccionado.
(Leyendo la base de datos ...
345011 ficheros y directorios instalados actualmente.)
Desempaquetando libflashsupport (de .../libflashsupport_1.9-0ubuntu1_i386.deb) ...
Configurando libflashsupport (1.9-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
cammell@cammell-laptop:~$

---

