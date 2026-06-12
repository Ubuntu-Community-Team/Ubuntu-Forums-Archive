---
title: "i can't instal brasero"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by jfca283 on 2007-03-09
i get this
```
juan@juan-desktop:~$ sudo apt-get install ./Desktop/brasero_0.5.1-1getdeb1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package .
juan@juan-desktop:~$ sudo dpkg -i ./Desktop/brasero_0.5.1-1getdeb1_i386.deb Selecting previously deselected package brasero.
(Reading database ... 112075 files and directories currently installed.)
Unpacking brasero (from .../brasero_0.5.1-1getdeb1_i386.deb) ...
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on libatk1.0-0 (>= 1.12.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 brasero depends on libavahi-client3 (>= 0.6.13); however:
  Version of libavahi-client3 on system is 0.6.10-0ubuntu3.4.
 brasero depends on libavahi-glib1 (>= 0.6.12); however:
  Version of libavahi-glib1 on system is 0.6.10-0ubuntu3.4.
 brasero depends on libbeagle0 (>= 0.2.9); however:
  Version of libbeagle0 on system is 0.2.6-1ubuntu5.
 brasero depends on libbonobo2-0 (>= 2.15.0); however:
  Version of libbonobo2-0 on system is 2.14.0-0ubuntu2.
 brasero depends on libbonoboui2-0 (>= 2.15.0); however:
  Version of libbonoboui2-0 on system is 2.14.0-0ubuntu1.
 brasero depends on libburn2 (>= 0.2.2); however:
  Package libburn2 is not installed.
 brasero depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 brasero depends on libcairo2 (>= 1.2.4); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.
 brasero depends on libdbus-1-3; however:
  Package libdbus-1-3 is not installed.
 brasero depends on libdbus-glib-1-2 (>= 0.71); however:
  Version of libdbus-glib-1-2 on system is 0.60-6ubuntu8.1.
 brasero depends on libfreetype6 (>= 2.2); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.2.
 brasero depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 brasero depends on libgnome-keyring0 (>= 0.5.2); however:
  Version of libgnome-keyring0 on system is 0.4.9-1ubuntu1.
 brasero depends on libgnomevfs2-0 (>= 2.15.90); however:
  Version of libgnomevfs2-0 on system is 2.14.2-0ubuntu1.
 brasero depends on libgnutls13 (>= 1.4.0-0); however:
  Package libgnutls13 is not installed.
 brasero depends on libgpg-error0 (>= 1.2); however:
  Version of libgpg-error0 on system is 1.1-4.
 brasero depends on libgstreamer-plugins-base0.10-0 (>= 0.10.10); however:
  Version of libgstreamer-plugins-base0.10-0 on system is 0.10.7-0ubuntu5.
 brasero depends on libgstreamer0.10-0 (>= 0.10.10); however:
  Version of libgstreamer0.10-0 on system is 0.10.6-0ubuntu2.
 brasero depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
 brasero depends on libisofs2 (>= 0.2.2); however:
  Package libisofs2 is not installed.
 brasero depends on libnautilus-burn4 (>= 2.15.3); however:
  Package libnautilus-burn4 is not installed.
 brasero depends on liborbit2 (>= 1:2.14.1); however:
  Version of liborbit2 on system is 1:2.14.0-0ubuntu1.
 brasero depends on libpango1.0-0 (>= 1.14.5); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
 brasero depends on libpopt0 (>= 1.10); however:
  Version of libpopt0 on system is 1.7-5.
 brasero depends on libselinux1 (>= 1.30); however:
  Version of libselinux1 on system is 1.28-2ubuntu2.
 brasero depends on libtasn1-3 (>= 0.3.4); however:
  Package libtasn1-3 is not installed.
 brasero depends on libtotem-plparser1 (>= 2.16.1); however:
  Version of libtotem-plparser1 on system is 1.4.3-0ubuntu1.
 brasero depends on libxml2 (>= 2.6.26); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
dpkg: error processing brasero (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 brasero
```

i always get problems with libraries
like 
libatk1
some versions of others
this is because my sources list is bad?
this are my repositories
```


deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://cl.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted
deb http://cl.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://seveas.imbrandon.com dapper-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb http://cl.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free

deb http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse
deb http://espergreen.com/apt dapper main
deb http://acorbeaux.free.fr/ubuntu edgy transmission
deb http://malteo.homelinux.net dapper-malteo extras
deb http://download.tuxfamily.org/3v1deb dapper 3v1n0
deb-src http://download.tuxfamily.org/3v1deb dapper 3v1n0
```

i mean, this problem is continuos
in every package who is a litle bit modern..problem
i can't install it
and i want to prove brasero
that's all i want
thanks for your help guys

---

