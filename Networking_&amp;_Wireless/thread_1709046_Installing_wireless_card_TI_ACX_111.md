---
title: "Installing wireless card TI ACX 111"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by iDrago on 2011-03-17
Hello,

 I recently installed the latest version of Ubuntu because I want to switch to Linux.
 The installation went well and now I want to connect to the Internet.
 However, it is necessary that I install the drivers for my wireless card, but I do not know how.
 I started reading the documentation, but I soon was dropped, I began.
 My wireless card: **Texas Instruments - ACX 111**
 I said that I use a WEP key, I understood that was important in the documentation.
 I also want to say I have no wired network near my computer so I am forced to log into Wifi connection.
 Can you help me install my wireless card?

 Sincerely, [B]iDrago ;-)
[/B]

---

### Post by chili555 on 2011-03-17
Please check here, especially, post #13.

[http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx&page=2](http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx&page=2)

Post back if you need more help.

---

### Post by dmizer on 2011-03-18
I do not have this card anymore, but this should still work: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

It will not work in 64bit though, as there are no 64bit drivers for this card at all ... anywhere ... even in Windows.

---

### Post by iDrago on 2011-03-18
I have a problem when I want to install ndiswrapper. Apparently he does not find the command "aptitude". Then I try with apt-get. Then they ask me to insert the Ubuntu CD, what I do. I get an error from the CD. Then he can not access the site from Ubuntu because I have no wired connection. I give you the log of the terminal.

```
idrago@Ordinateur:~$ sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
sudo: aptitude: command not found
idrago@Ordinateur:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Paquets suggérés :
  ndiswrapper-source ndiswrapper-dkms
Les NOUVEAUX paquets suivants seront installés :
  ndiswrapper-common ndiswrapper-utils-1.9
0 mis à jour, 2 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0o/57,7ko dans les archives.
Après cette opération, 225ko d'espace disque supplémentaires seront utilisés.
Changement de support : veuillez insérer le disque
« Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) »
dans le lecteur « /cdrom/ » et appuyez sur la touche Entrée

Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main ndiswrapper-utils-1.9 i386 1.56-3
  Fichier non trouvé
Err http://fr.archive.ubuntu.com/ubuntu/ maverick/main ndiswrapper-utils-1.9 i386 1.56-3
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56-3_i386.deb  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
E: Impossible de récupérer quelques archives, peut-être devrez-vous lancer apt-get update ou essayer avec --fix-missing ?
```

---

### Post by chili555 on 2011-03-18
Please drop the CD in the tray and try:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

```

---

### Post by iDrago on 2011-03-18
```
idrago@Ordinateur:~$ sudo apt-cdrom add
Utilisation du point de montage /media/apt/ pour le cédérom
Identification...[72afd8d176d51dd88e31b7d4f0ed516f-2]
Examen du disque à la recherche de fichiers d'index...
2 index de paquets trouvés, 0 index de sources, 0 index de traductions et 1 signatures
Ce disque s'appelle :
« Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) »
Copie des listes de paquets...gpgv: Signature faite le jeu. 07 oct. 2010 18:24:55 CEST avec la clé DSA ID FBB75451
gpgv: Bonne signature de « Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com> »
Reading Package Indexes... Fait
Écriture de la nouvelle liste de sources
Les entrées de listes de sources pour ce disque sont :
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
Veuillez répéter cette opération pour tous les disques de votre jeu de cédéroms.
W: Fichier /media/apt/dists/maverick/main/binary-i386/Packages inexistant ignoré
W: Fichier /media/apt/dists/maverick/restricted/binary-i386/Packages inexistant ignoré
idrago@Ordinateur:~$ sudo apt-get update
Err http://fr.archive.ubuntu.com maverick Release.gpg
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick/main Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick/universe Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com maverick-updates Release.gpg
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://extras.ubuntu.com maverick Release.gpg
  Ne parvient pas à résoudre « extras.ubuntu.com »
Err http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
  Ne parvient pas à résoudre « extras.ubuntu.com »
Err http://extras.ubuntu.com/ubuntu/ maverick/main Translation-fr
  Ne parvient pas à résoudre « extras.ubuntu.com »
Err http://security.ubuntu.com maverick-security Release.gpg
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-fr
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-fr
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-fr
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-fr
  Ne parvient pas à résoudre « security.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Err http://fr.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-fr
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-fr
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-fr
Lecture des listes de paquets... Fait
W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « fr.archive.ubuntu.com »

W: Impossible de récupérer http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Ne parvient pas à résoudre « extras.ubuntu.com »

W: Impossible de récupérer http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Ne parvient pas à résoudre « extras.ubuntu.com »

W: Impossible de récupérer http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « extras.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Impossible de récupérer http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-fr.bz2  Ne parvient pas à résoudre « security.ubuntu.com »

W: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.
idrago@Ordinateur:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Paquets suggérés :
  ndiswrapper-source ndiswrapper-dkms
Les NOUVEAUX paquets suivants seront installés :
  ndiswrapper-common ndiswrapper-utils-1.9
0 mis à jour, 2 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0o/57,7ko dans les archives.
Après cette opération, 225ko d'espace disque supplémentaires seront utilisés.
Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main ndiswrapper-utils-1.9 i386 1.56-3
  Fichier non trouvé
Err http://fr.archive.ubuntu.com/ubuntu/ maverick/main ndiswrapper-utils-1.9 i386 1.56-3
  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56-3_i386.deb  Ne parvient pas à résoudre « fr.archive.ubuntu.com »
E: Impossible de récupérer quelques archives, peut-être devrez-vous lancer apt-get update ou essayer avec --fix-missing ?

```

---

### Post by chili555 on 2011-03-18
I'm not too sure what went wrong. When you added the CD, did it create an icon on your desktop labeled Ubuntu 10.10 i386? Can you right-click it and select Open and browse to pool/main/n/ndiswrapper? The two packages are in there and you should be able to right-click them and select Open with Ubuntu Software Center.

---

### Post by iDrago on 2011-03-18
Finally, I downloaded these two packages that I put on a USB key and so I was able to install Ndiswrapper.

[http://packages.ubuntu.com/maverick/ndiswrapper-common](http://packages.ubuntu.com/maverick/ndiswrapper-common)
[http://packages.ubuntu.com/maverick/ndiswrapper-utils-1.9](http://packages.ubuntu.com/maverick/ndiswrapper-utils-1.9)

Edit : But with iwconfig, nothing is detected.

---

### Post by chili555 on 2011-03-18
> But with iwconfig, nothing is detected.You need to install the Windows XP .inf and (probably) .sys files for ndiswrapper to work. Do you have them?> Ahhh.. it feels great to be on ubuntu again!

Here's what I did:
1) Installed 32-bit version of ubuntu 9.10
2) Installed NDISwrapper from the live-CD (the one you install ubuntu with)
3) [COLOR="Red"]Popped in the CD with the drivers, and copied them over to a location in ubuntu.[/COLOR]
4) Opened NDISwrapper (System > Administration > Windows Wireless Drivers)
5) [COLOR="Red"]Selected the tnet1130.INF file, selected OK[/COLOR]
6) Used ubuntu's default network manager (Network Manager, on the top right) and connected to my network!

---

### Post by iDrago on 2011-03-18
I succeeded to step 5, but then I do not find.

---

### Post by chili555 on 2011-03-18
What do the drivers on the CD look like? Are they in a folder? Are they in a zip file? Or...what?

---

### Post by iDrago on 2011-03-18
On the CD, there is a drivers folder with multiple folders inside : Windows 98, Windows 2000, Windows ME and Windows XP. I took the files from Windows XP.

---

### Post by chili555 on 2011-03-18
And what are the files in there? Please run and post:```
ndiswrapper -l
```That is an l for 'list.'

---

### Post by iDrago on 2011-03-18
FW1130.bin ; FwRad16.bin ; FwRad17.bin ; TNET1130.INF ; tnet1130.sys

```
idrago@Ordinateur:~$ ndiswrapper -l
tnee1130 : driver installed
    device (104C:9066) 

```

---

### Post by chili555 on 2011-03-18
Tres bien! Drag and drop the XP folder to your desktop and then:> 4) Opened NDISwrapper (System > Administration > Windows Wireless Drivers)
5) Selected the [COLOR="Red"]TNET[/COLOR]1130.INF file, selected OK
6) Used ubuntu's default network manager (Network Manager, on the top right) and connected to my network! Post back; I'm here for you.

---

### Post by iDrago on 2011-03-18
Nice French ;)
After selecting the  TNET1130.INF file and click on Ok, I get an error message but the configuration is still added.

```
Le module ne peut pas être chargé. L'erreur était:

FATAL: Could not read '/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory
```

```
idrago@Ordinateur:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

idrago@Ordinateur:~$ ndiswrapper -l
tnet1130 : driver installed
    device (104C:9066) present
```

---

### Post by chili555 on 2011-03-18
> Could not read '/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directoryThat's a new one on me, mon ami. Please open a terminal and navigate to the directory where you downloaded the files:> Finally, I downloaded these two packages that I put on a USB key and so I was able to install Ndiswrapper.

[http://packages.ubuntu.com/maverick/ndiswrapper-common](http://packages.ubuntu.com/maverick/ndiswrapper-common)
[http://packages.ubuntu.com/maverick/...pper-utils-1.9](http://packages.ubuntu.com/maverick/...pper-utils-1.9)Desktop? Downloads? I assume your language of choice is French, so use the correct term, if it's not desktop:```
cd Desktop
```Now let's reinstall both of the packages and see if our error goes away:```
sudo dpkg -i ndis*
```The wildcard * will include everything on your desktop that starts with ndis. If the terminal reports they are both installed, I think we'll have to look deeper. Check with:```
sudo modprobe ndiswrapper
iwconfig
```

Bon chance.

My French is barely useable after high school 50 years ago!

---

### Post by chili555 on 2011-03-18
Please run:```
sudo dpkg -s libc6
```Does it say: Status: install ok installed ?

---

### Post by iDrago on 2011-03-19
```
idrago@Ordinateur:~$ cd Bureau
idrago@Ordinateur:~/Bureau$ sudo dpkg -i ndis*
(Lecture de la base de données... 118636 fichiers et répertoires déjà installés.)
Préparation du remplacement de ndiswrapper-common 1.56-3 (en utilisant ndiswrapper-common_1.56-3_all.deb) ...
Dépaquetage de la mise à jour de ndiswrapper-common ...
Préparation du remplacement de ndiswrapper-utils-1.9 1.56-3 (en utilisant ndiswrapper-utils-1.9_1.56-3_i386.deb) ...
Dépaquetage de la mise à jour de ndiswrapper-utils-1.9 ...
Paramétrage de ndiswrapper-common (1.56-3) ...
Traitement des actions différées (« triggers ») pour « man-db »...
Paramétrage de ndiswrapper-utils-1.9 (1.56-3) ...
idrago@Ordinateur:~/Bureau$ sudo modprobe ndiswrapper
FATAL: Could not read '/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory
idrago@Ordinateur:~/Bureau$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

idrago@Ordinateur:~/Bureau$ sudo dpkg -s libc6
Package: libc6
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 9480
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: eglibc
Version: 2.12.1-0ubuntu6
Replaces: belocs-locales-bin
Provides: glibc-2.11-1, libc6-i686
Depends: libc-bin (= 2.12.1-0ubuntu6), libgcc1, tzdata, findutils (>= 4.4.0-2ubuntu2)
Suggests: glibc-doc, debconf | debconf-2.0, locales
Breaks: nscd (<< 2.12)
Conflicts: belocs-locales-bin, libc6-i686, tzdata (<< 2007k-1), tzdata-etch
Conffiles:
 /etc/ld.so.conf.d/i686-linux-gnu.conf 6b67198f6b0c62a07fa422cb222a4341
Description: Embedded GNU C Library: Shared libraries
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others.
Homepage: http://www.eglibc.org
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
idrago@Ordinateur:~/Bureau$ sudo modprobe ndiswrapper
FATAL: Could not read '/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory
idrago@Ordinateur:~/Bureau$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by orrymr on 2011-03-19
Just googled "FATAL: Could not read '/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory" and it directed me here -> having the same problem. I'll let you know if I find a fix

---

### Post by orrymr on 2011-03-19
What does the "sudo dpkg -s libc6" command do?

---

### Post by chili555 on 2011-03-19
It's the craziest thing I've seen in a while. libc6 is required for ndiswrapper and, of course, the two things depend on each other. All are properly installed. Please do:```
sudo updatedb
locate ndiswrapper.ko
uname -r
```updatedb will take a few moments, be patient.

Next, if the file is actually found, we ought to look at ownership and permissions:```
ls -al /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

---

### Post by chili555 on 2011-03-19
> **orrymr said:**
> What does the "sudo dpkg -s libc6" command do?It determines the status (-s) of the package libc6. In the OP's case, it shows as "Status: install ok installed" I was interested because it is a dependency of ndiswrapper. If libc6 was not installed or broken, ndiswrapper wouldn't work correctly. Actually, I believe that libc6 is a needed part of every installation, but I have seen stranger things in my life!

---

### Post by iDrago on 2011-03-19
```
idrago@Ordinateur:~$ sudo updatedb
idrago@Ordinateur:~$ locate ndiswrapper.ko
idrago@Ordinateur:~$ uname -r
2.6.35-22-generic
idrago@Ordinateur:~$ ls -al /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
ls: ne peut accéder /lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko: Aucun fichier ou dossier de ce type
idrago@Ordinateur:~$ 

```

---

### Post by chili555 on 2011-03-19
I tried the same process as you; download the packages and install. I also get 'module not found' and this:```
 sudo ndiswrapper -v
ERROR: modinfo: could not find module ndiswrapper
**module version is too old!**
utils version: '1.9', utils version needed by module: '0'
module details:
ERROR: modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net

```I am very surprised because this was the Ubuntu Maverick version we just downloaded. I am googling and hope someone will chime in with an answer.

---

### Post by iDrago on 2011-03-19
I saw that several people had the same problem. I await your reply ^^

---

### Post by orrymr on 2011-03-19
Shouldn't ndiswrapper.ko get compiled and inserted into \kernel\ubuntu\ndiswrapper at installation? That folder is empty...

---

### Post by chili555 on 2011-03-19
> **orrymr said:**
> Shouldn't ndiswrapper.ko get compiled and inserted into \kernel\ubuntu\ndiswrapper at installation? That folder is empty...Yes, indeed, it should. We're scratching our gray beards trying to figure out why it isn't.

---

### Post by orrymr on 2011-03-19
What if someone just uploads it somewhere? Can't we just manually copy n paste it into the relevant folder? Or does it *have* to be compiled?

---

### Post by chili555 on 2011-03-19
> **orrymr said:**
> What if someone just uploads it somewhere? Can't we just manually copy n paste it into the relevant folder? Or does it *have* to be compiled?Doubtful:>  sudo cp /lib/modules/2.6.35-27-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko /lib/modules/2.6.35-28-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
[sudo] password for chili: 
cp: cannot create regular file `/lib/modules/2.6.35-28-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directoryThe whole structure is missing. 

I am stumped, frankly.

---

### Post by orrymr on 2011-03-20
will (very) old versions on ndiswrapper work with meerkat?

---

### Post by iDrago on 2011-03-21
I allow myself to make a up to know if there is the new one.

---

### Post by dmizer on 2011-03-21
Ok, the driver for this card has errors in it, and you need to fix them. That's why I posted my tutorial. Unless you fix the errors in the driver, the ndiswrapper module won't load.

First of all, please remove any and all drivers you've tried to load into ndiswrapper.

Then, take a look at my tutorial here: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148) and start from step 4 under "Prepare the windows driver."

---

### Post by orrymr on 2011-03-22
What I ended up doing is reinstalling ubuntu from scratch. Something must have gone wrong during installation since ndiswrapper.ko wasn't present. After I reinstalled ndiswrapper.ko was there even before I installed ndiswrapper common and util.

---

### Post by iDrago on 2011-03-22
@dmizer

```
idrago@Ordinateur:~$ mkdir linksys
idrago@Ordinateur:~$ cd linksys
idrago@Ordinateur:~/linksys$ mv tnet1130.sys TNET1130.sys
idrago@Ordinateur:~/linksys$ sed -e 's/tnet1130.sys/TNET1130.sys/' TNET1130.INF > TNET1130.new&& mv TNET1130.new TNET1130.INF
idrago@Ordinateur:~/linksys$ sudo ndiswrapper -i TNET1130.INF
installing tnet1130 ...
idrago@Ordinateur:~/linksys$ sudo modprobe ndiswrapper
FATAL: Could not read '/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory

```

---

### Post by dmizer on 2011-03-22
Are you using a 64bit Ubuntu?

---

### Post by iDrago on 2011-03-22
```
Linux Ordinateur 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
```

So no.

---

### Post by dmizer on 2011-03-22
What is the output of:
```
sudo ndiswrapper -v
```

---

### Post by iDrago on 2011-03-22
```
idrago@Ordinateur:~$ sudo ndiswrapper -v
ERROR: modinfo: could not open /lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko: No such file or directory
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
ERROR: modinfo: could not open /lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko: No such file or directory

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
```

---

### Post by dmizer on 2011-03-22
Remove the TNET1130.INF as a driver and install both lsbcmnds.inf and LSTINDS.INF instead.

---

### Post by iDrago on 2011-03-23
```
idrago@Ordinateur:~$ cd linksys
idrago@Ordinateur:~/linksys$ mv tnet1130.sys TNET1130.sys
idrago@Ordinateur:~/linksys$ sed -e 's/tnet1130.sys/TNET1130.sys/' LSTINDS.INF > LSTINDS.new&& mv LSTINDS.new LSTINDS.INF
idrago@Ordinateur:~/linksys$ sudo ndiswrapper -i lsbcmnds.inf
installing lsbcmnds ...
idrago@Ordinateur:~/linksys$ sudo ndiswrapper -i LSTINDS.INF
installing lstinds ...
idrago@Ordinateur:~/linksys$ sudo modprobe ndiswrapper
FATAL: Could not read '/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory

```

---

### Post by dmizer on 2011-03-23
OK, now I'm stuck. At this point, it should work correctly.

I suggest asking for help in this thread: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by pytheas22 on 2011-03-24
> **dmizer said:**
> OK, now I'm stuck. At this point, it should work correctly.

I suggest asking for help in this thread: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

Taking the easy way out :)

Actually I found this thread because I was googling trying to figure out the problem myself.  It's bizarre, but this is the second time I've seen it this week, in both cases with kernel 2.6.35-22-generic.

My thought is that compiling ndiswrapper from source should put the module in place.  That is what I've asked iDrago to do [here]("http://ubuntuforums.org/showthread.php?t=885847&page=99"); hopefully it will work.

Also, for the record, I have kernel 2.6.35-22-generic installed on my system, and it's the i686 build just like iDrago's, yet ndiswrapper.ko exists there.  It's really strange that it's disappearing on other people.

---

### Post by dmizer on 2011-03-25
> **pytheas22 said:**
> Taking the easy way out :)
When in doubt, refer to the experts ;)

I had it happen before because I had the wrong driver installed but I know that's not the case here.

Thanks for the followup.

---

### Post by iDrago on 2011-04-02
Hey, I'm back after a week of absence due to cutting my internet connection. Again sorry for the absence. Moving on.

 I finally managed to log into WiFi. I reinstalled Ubuntu but this time the 10.04.2 LTS version. Then I install **ndiswrapper** files present on the installation CD. To install, simply double-click it.

```
pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb
pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb
```They can also be downloaded here:

```
http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb
http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb
```Then I install **ndisgtk** in the same way.

```
pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb
```They can also be downloaded here:

```
http://mirrors.kernel.org/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb
```

Then simply install the Windows driver through the GUI ndisgkt, configure it and we can connect.

---

### Post by pytheas22 on 2011-04-02
**iDrago**: thanks for letting us know how you got it sorted out.  It makes sense that a reinstallation of Ubuntu took care of the issue, because the root of the problem was that the ndiswrapper module was missing from your kernel for some bizarre reason.

I'm still curious as to how your ndiswrapper module disappeared in the first place (because you're not the only user I've seen recently with that problem, suggesting there's a bug lurking somewhere that's causing this), but in any case I'm glad to hear you're online now.  Enjoy Ubuntu :)

---

