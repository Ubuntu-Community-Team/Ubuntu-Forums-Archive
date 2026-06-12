---
title: "Problem with BCM 43142 on ASUS f201E"
date: 2013-09-02
forum: Networking &amp; Wireless
---

### Post by jhon3 on 2013-09-02
I don't speak english very well, i speak spanish, i writing for help. i  have a asus f201e, but when I bought them was delivered with windows.  I've never used Ubuntu, I installed 12.04.3, it was not easy to place  the double start, but after following many links, I found the solution,  now the problem I have is with the wifi (BCM 43142, 14E4: 4365), does  not work. I searched many solutions but none works, the last one was  followed [http://ubuntuforums.org/showthread.php?t=2123154](http://ubuntuforums.org/showthread.php?t=2123154) but neither worked for me. write what appeared if you can help. thanks in advance.

jhon@minjhongomez:~$ sudo apt-get install linux-headers-generic build-essential dkms
[sudo] password for jhon: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
build-essential ya está en su versión más reciente.
dkms ya está en su versión más reciente.
linux-headers-generic ya está en su versión más reciente.
Tal vez quiera ejecutar «apt-get -f install» para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
 linux-backports-modules-cw-3.6-quantal-generic : Depende: linux-backports-modules-cw-3.6-3.5.0-40-generic pero no es instalable
E: Dependencias incumplidas. Intente «apt-get -f install» sin paquetes (o especifique una solución).
jhon@minjhongomez:~$ sudo apt-get install --reinstall linux-headers-generic
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt-get -f install» para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
 linux-backports-modules-cw-3.6-quantal-generic : Depende: linux-backports-modules-cw-3.6-3.5.0-40-generic pero no es instalable
E: Dependencias incumplidas. Intente «apt-get -f install» sin paquetes (o especifique una solución).
jhon@minjhongomez:~$ sudo apt-get install --reinstall linux-headers-`uname -r`
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt-get -f install» para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
 linux-backports-modules-cw-3.6-quantal-generic : Depende: linux-backports-modules-cw-3.6-3.5.0-40-generic pero no es instalable
E: Dependencias incumplidas. Intente «apt-get -f install» sin paquetes (o especifique una solución).
jhon@minjhongomez:~$ cd Descargas
jhon@minjhongomez:~/Descargas$ sudo dpkg -i wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb
(Leyendo la base de datos ... 207627 ficheros o directorios instalados actualmente.)
Preparando para reemplazar wireless-bcm43142-dkms 6.20.55.19-1 (usando wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb) ...

------------------------------
Deleting module version: 6.20.55.19
completely from the DKMS tree.
------------------------------
Done.
Desempaquetando el reemplazo de wireless-bcm43142-dkms ...
Configurando wireless-bcm43142-dkms (6.20.55.19-1) ...
Loading new wireless-bcm43142-6.20.55.19 DKMS files...
Building only for 3.8.0-29-generic
Building initial module for 3.8.0-29-generic
Error! Bad return status for module build on kernel: 3.8.0-29-generic (x86_64)
Consult /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/make.log for more information.

---

### Post by chili555 on 2013-09-02
Please see my private message.

---

