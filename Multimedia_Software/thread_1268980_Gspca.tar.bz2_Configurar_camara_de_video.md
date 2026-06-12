---
title: "Gspca.tar.bz2 Configurar camara de video"
date: 2009-09-17
forum: Multimedia Software
---

### Post by evalckea on 2009-09-17
Hola amigos,
Tengo un problemita que no he podido solucionar con mis Webcam, despues de mucho investigar he encontrado que la solución está en compilar los modulos que se encuentran en el archivo /usr/src/gspca.tar.bz2, despues de mucho buscar encontré como hacerlo en la página [http://diegotorquemada-linux.blogspot.com/](http://diegotorquemada-linux.blogspot.com/) bajo el título Configura Webcam Genius eye 110 en Debian Lenny, sigo los pasos me en la siguiente forma:
$ /usr/src$ sudo tar jxvf gspca.tar.bz2 modules/
modules/gspca/
modules/gspca/debian/
modules/gspca/debian/rules
modules/gspca/debian/control.modules.in
modules/gspca/debian/postinst.modules.in
modules/gspca/debian/control
modules/gspca/debian/compat
modules/gspca/debian/copyright
modules/gspca/debian/changelog
modules/gspca/Mars-Semi/
modules/gspca/Mars-Semi/mr97311.h
modules/gspca/decoder/
modules/gspca/decoder/gspcadecoder-OSX.c
modules/gspca/decoder/gspcadecoder.c
modules/gspca/decoder/gspcadecoder-OSX.h
modules/gspca/decoder/gspcadecoder.h
modules/gspca/Transvision/
modules/gspca/Transvision/tv8532.h
modules/gspca/Sonix/
modules/gspca/Sonix/sonix.h
modules/gspca/Sonix/sn9cxxx.h
modules/gspca/Sunplus/
modules/gspca/Sunplus/spca561.h
modules/gspca/Sunplus/spca501_init.h
modules/gspca/Sunplus/spca501.dat
modules/gspca/Sunplus/spca506.h
modules/gspca/Sunplus/spca508.dat
modules/gspca/Sunplus/spca508_init-OSX.h
modules/gspca/Sunplus/spca501_init-OSX.h
modules/gspca/Sunplus/spca505_init.h
modules/gspca/Sunplus/spca508_init.h
modules/gspca/Sunplus/spca561-OSX.h
modules/gspca/Sunplus/spca505.dat
modules/gspca/utils/
modules/gspca/utils/spcaCompat.h
modules/gspca/utils/spcagamma.h
modules/gspca/utils/spcausb.h
modules/gspca/Etoms/
modules/gspca/Etoms/et61xx51.h
modules/gspca/Sunplus-jpeg/
modules/gspca/Sunplus-jpeg/sp5xxfw2.h
modules/gspca/Sunplus-jpeg/spca500_init.h
modules/gspca/Sunplus-jpeg/sp5xxfw2.dat
modules/gspca/Sunplus-jpeg/jpeg_qtables.h
modules/gspca/Sunplus-jpeg/spca500.dat
modules/gspca/Vimicro/
modules/gspca/Vimicro/pas106b.h
modules/gspca/Vimicro/ov7620.h
modules/gspca/Vimicro/vc032x_sensor.h
modules/gspca/Vimicro/pb0330.h
modules/gspca/Vimicro/tas5130c_vf0250.h
modules/gspca/Vimicro/tas5130c.h
modules/gspca/Vimicro/cs2102.h
modules/gspca/Vimicro/vc032x.h
modules/gspca/Vimicro/hv7131c.h
modules/gspca/Vimicro/zc3xx.h
modules/gspca/Vimicro/hdcs2020.h
modules/gspca/Vimicro/ov7630c.h
modules/gspca/Vimicro/icm105a.h
modules/gspca/Vimicro/hv7131b.h
modules/gspca/Vimicro/mc501cb.h
modules/gspca/Pixart/
modules/gspca/Pixart/pac7311.h
modules/gspca/Pixart/pac207-OSX.h
modules/gspca/Pixart/pac207.h
modules/gspca/Conexant/
modules/gspca/Conexant/cx11646.h
modules/gspca/Conexant/cxlib.h
modules/gspca/Makefile.kld
modules/gspca/cutlog.py
modules/gspca/gspca_core.c
modules/gspca/READ_AND_INSTALL
modules/gspca/gspca_build
modules/gspca/Makefile
modules/gspca/changelog
modules/gspca/gspca.h
modules/gspca/license
$ /usr/src$ cd modules/
$ /usr/src/modules$ cd gspca/
$ /usr/src/modules/gspca$ sudo m-a prepare
Obteniendo los fuentes de la versión del núcleo: 2.6.28-15-generic
Encabezados del núcleo disponibles en /usr/src/linux
Creando enlace simbólico...
¡No se pudo crear el enlace simbólico /usr/src/linux!
apt-get install build-essential 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
build-essential ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

¡Hecho!
$ /usr/src/modules/gspca$ sudo m-a a-i gspca
Actualizado los ficheros infos de los paquetes 1
Obteniendo los fuentes de la versión del núcleo: 2.6.28-15-generic
Encabezados del núcleo disponibles en /usr/src/linux-headers-2.6.28-15-generic
Creando enlace simbólico...
apt-get install build-essential 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
build-essential ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

¡Hecho!
unpack 
Extracting the package tarball, /usr/src/gspca.tar.bz2, please wait...
"/usr/share/modass/overrides/gspca-source" build KVERS=2.6.28-15-generic KSRC=/usr/src/linux KDREV=2.6.28-15.49 kdist_image

Y hasta aqui puedo llegar, el hecho es que no me compila y por lo tanto mi Webcam continua fuera.
Agradezco su ayuda.

Cordialmente,
Efraim
Jamundí - Colombia

---

### Post by evalckea on 2009-09-20
Lo resolví instalando Hardy Heron 8.04 LTS, en este pude configurar mi camara, no entiendo la razón por la cual me fue imposible en en Jaunty 9-04

---

