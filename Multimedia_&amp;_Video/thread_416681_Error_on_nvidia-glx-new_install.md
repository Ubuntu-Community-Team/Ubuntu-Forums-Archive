---
title: "Error on nvidia-glx-new install"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by CyberSDF on 2007-04-21
Hello !

After upgrading edgy to festy, i try to install the package nvidia-glx-new but i have the following message :

```
Dépaquetage de nvidia-glx-new (à partir de .../nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb) ...
dpkg-divert: « diversion of /usr/lib/xorg/modules/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-new » entre en conflit avec « diversion of /usr/lib/xorg/modules/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx »
dpkg : erreur de traitement de /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb (--unpack) :
 le sous-processus pre-installation script a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I can't find why this message and how to reprair it.

Have you any idea to resolve it ?

---

### Post by zeroblitzt on 2007-04-21
I get the same error, except when trying to install the nvidia-glx-legacy driver.

As a result, I can only use my system in text mode because the X server wont start.

---

### Post by CyberSDF on 2007-04-21
For information :
- I have none broken package
- I try with other source for the deb
- no dependances problem
- x work fine with nv driver

---

### Post by CyberSDF on 2007-04-21
It seem an OpenGL problem :
```
$ glxgears 
glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

---

### Post by CyberSDF on 2007-04-21
Bad way...

New approch :

I have the message :
> dpkg-divert: « diversion of /usr/lib/xorg/modules/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-new » entre en conflit avec « diversion of /usr/lib/xorg/modules/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx »
Let's see :
```
$ ls -l /usr/lib/xorg/modules/libGL*
ls: /usr/lib/xorg/modules/libGL*: Aucun fichier ou répertoire de ce type
```
???

far away :
```
$ sudo apt-file search libGLcore.so
nvidia-glx: usr/lib/libGLcore.so.1
nvidia-glx: usr/lib/libGLcore.so.1.0.9631
nvidia-glx-legacy: usr/lib/libGLcore.so.1
nvidia-glx-legacy: usr/lib/libGLcore.so.1.0.7184
nvidia-glx-new: usr/lib/libGLcore.so.1
nvidia-glx-new: usr/lib/libGLcore.so.1.0.9755
xserver-xorg-core: usr/lib/xorg/modules/extensions/libGLcore.so
```
Maybe a bad installation of xserver-xorg-core ?
```
$ sudo apt-get install --reinstall xserver-xorg-core
[code]$ sudo dpkg-reconfigure xserver-xorg-core
```
let's see :
```
$ ls -l /usr/lib/xorg/modules/libGL*
ls: /usr/lib/xorg/modules/libGL*: Aucun fichier ou répertoire de ce type
```
Strange... 

Just try again
```
$ sudo apt-get install nvidia-glx-new
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture de l'information d'état... Fait
Paquets suggérés :
  nvidia-settings nvidia-new-kernel-source
Les NOUVEAUX paquets suivants seront installés :
  nvidia-glx-new
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0o/4833ko dans les archives.
Après dépaquetage, 14,7Mo d'espace disque supplémentaires seront utilisés.
(Lecture de la base de données... 123010 fichiers et répertoires déjà installés.)
Dépaquetage de nvidia-glx-new (à partir de .../nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb) ...
dpkg-divert: « diversion of /usr/lib/xorg/modules/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-new » entre en conflit avec « diversion of /usr/lib/xorg/modules/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx »
dpkg : erreur de traitement de /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb (--unpack) :
 le sous-processus pre-installation script a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Grrrr...

And the old one ?

```
$ sudo apt-get install nvidia-glx
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture de l'information d'état... Fait
Paquets suggérés :
  nvidia-kernel-source
Les NOUVEAUX paquets suivants seront installés :
  nvidia-glx
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0o/4492ko dans les archives.
Après dépaquetage, 13,7Mo d'espace disque supplémentaires seront utilisés.
(Lecture de la base de données... 123010 fichiers et répertoires déjà installés.)
Dépaquetage de nvidia-glx (à partir de .../nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb) ...
dpkg-divert: « diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx » entre en conflit avec « diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new »
dpkg : erreur de traitement de /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb (--unpack) :
 le sous-processus pre-installation script a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

New place of libGL.so ? Let's see :
```
$ ls /usr/lib/libGL*
/usr/lib/libGLEW.so.1.3  /usr/lib/libGLEW.so.1.3.4  /usr/lib/libGLU.a  /usr/lib/libGLU.so  /usr/lib/libGLU.so.1  /usr/lib/libGLU.so.1.3.060502
```
?????

```
>$ sudo apt-file search libGL.so
libgl1-mesa-dev: usr/lib/libGL.so
libgl1-mesa-glide3: usr/lib/i686/mmx/cmov/libGL.so.1
libgl1-mesa-glide3: usr/lib/i686/mmx/cmov/libGL.so.1.5.060201
libgl1-mesa-glide3: usr/lib/libGL.so.1
libgl1-mesa-glide3: usr/lib/libGL.so.1.5.060201
libgl1-mesa-glide3-dev: usr/lib/i686/mmx/cmov/libGL.so
libgl1-mesa-glide3-dev: usr/lib/libGL.so
libgl1-mesa-glx: usr/lib/libGL.so.1
libgl1-mesa-glx: usr/lib/libGL.so.1.2
libgl1-mesa-glx-dbg: usr/lib/debug/usr/lib/libGL.so.1.2
libgl1-mesa-swx11: usr/lib/libGL.so.1
libgl1-mesa-swx11: usr/lib/libGL.so.1.5.060502
libgl1-mesa-swx11-dbg: usr/lib/debug/usr/lib/libGL.so.1.5.060502
libgl1-mesa-swx11-dev: usr/lib/libGL.so
libgl1-mesa-swx11-i686: usr/lib/i686/cmov/libGL.so.1
libgl1-mesa-swx11-i686: usr/lib/i686/cmov/libGL.so.1.5.060502
lsb-build-base2: usr/lib/lsb2/libGL.so
lsb-build-base3: usr/lib/lsb3/libGL.so
nvidia-glx: usr/lib/libGL.so.1
nvidia-glx: usr/lib/libGL.so.1.0.9631
nvidia-glx-dev: usr/lib/libGL.so
nvidia-glx-legacy: usr/lib/libGL.so.1
nvidia-glx-legacy: usr/lib/libGL.so.1.0.7184
nvidia-glx-legacy-dev: usr/lib/libGL.so
nvidia-glx-new: usr/lib/libGL.so.1
nvidia-glx-new: usr/lib/libGL.so.1.0.9755
nvidia-glx-new-dev: usr/lib/libGL.so
xorg-driver-fglrx: usr/lib/libGL.so.1
xorg-driver-fglrx: usr/lib/libGL.so.1.2
```
Well well well...

```
$ sudo apt-get install --reinstall libgl1-mesa-dev libgl1-mesa-glx
```

And now ?
```
>$ ls /usr/lib/libGL.*
/usr/lib/libGL.so
```

Hum... try again :
```
>$ sudo apt-get install nvidia-glx
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture de l'information d'état... Fait
Paquets suggérés :
  nvidia-kernel-source
Les NOUVEAUX paquets suivants seront installés :
  nvidia-glx
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0o/4492ko dans les archives.
Après dépaquetage, 13,7Mo d'espace disque supplémentaires seront utilisés.
(Lecture de la base de données... 123010 fichiers et répertoires déjà installés.)
Dépaquetage de nvidia-glx (à partir de .../nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb) ...
dpkg-divert: « diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx » entre en conflit avec « diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new »
dpkg : erreur de traitement de /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb (--unpack) :
 le sous-processus pre-installation script a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

$ sudo apt-get install nvidia-glx-new
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture de l'information d'état... Fait
Paquets suggérés :
  nvidia-settings nvidia-new-kernel-source
Les NOUVEAUX paquets suivants seront installés :
  nvidia-glx-new
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0o/4833ko dans les archives.
Après dépaquetage, 14,7Mo d'espace disque supplémentaires seront utilisés.
(Lecture de la base de données... 123010 fichiers et répertoires déjà installés.)
Dépaquetage de nvidia-glx-new (à partir de .../nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb) ...
dpkg-divert: « diversion of /usr/lib/xorg/modules/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-new » entre en conflit avec « diversion of /usr/lib/xorg/modules/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx »
dpkg : erreur de traitement de /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb (--unpack) :
 le sous-processus pre-installation script a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


```
$ ll /usr/lib/libGL.*
lrwxrwxrwx 1 root root 10 2007-04-21 18:56 /usr/lib/libGL.so -> libGL.so.1
```
```
$ sudo updatedb
$ locate libGL.so.1
/usr/lib/nvidia/libGL.so.1.2.xlibmesa
/usr/lib/nvidia/libGL.so.1.xlibmesa
```
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by papabean on 2007-04-21
I appear to have gotten it working by doing the following:

```
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1.2
sudo dpkg-divert --remove /usr/lib/xorg/modules/libGLcore.so
sudo apt-get install nvidia-glx-new
```
Hope this helps

---

### Post by CyberSDF on 2007-04-21
It's help ! Juste one *dpkg-divert --remove* less but now it's work.
Juste some problem with 3D now, but i think it is an other thing.

Thank a lot !

---

### Post by flawedprefect on 2007-06-19
Dude, without knowing it, you solved my issue with Amarok, which depends on that file. Anyone else who is having issues with Amarok - namely, you try to run it, and it flashes its splash screen for a fraction of a second, then quits - this is a possible solution.

---

