---
title: "cannot transfer data using SCP"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by nobani on 2010-06-12
Dear user,
when I try to transfer a folder from the desktop machine  to laptop I get the following:
```

morad@linux-m9c6:~> cd /data/
morad@linux-m9c6:/data> scp -r nobani@192.168.1.3:/data/geant **.**
Password:
On this machine the G4SYSTEM=Linux-g++
morad@linux-m9c6:/data>

```were the geant directory is contain about 3 GB of data.
Also I cannot join the laptop from the desktop using SSH without any massage but the console be frozen, but I can join the desktop from the laptop.
note that I use this method several times.
please see below:
```

morad@linux-m9c6:~> ssh nobani@192.168.1.3
Password:
Last login: Sat Jun 12 19:34:47 2010 from 192.168.1.2
Have a lot of fun...
On this machine the G4SYSTEM=Linux-g++
On this machine the G4INSTALL=/data/geant/geant4.9.3
On this machine the G4LIB=/data/geant/geant4.9.3/lib
On this machine the G4LEVELGAMMADATA=/data/geant/geant4.9.3/data/PhotonEvaporation2.0
On this machine the G4RADIOACTIVEDATA=/data/geant/geant4.9.3/data/RadioactiveDecay3.2
On this machine the G4LEDATA=/data/geant/geant4.9.3/data/G4EMLOW6.9
On this machine the G4NEUTRONHPDATA=/data/geant/geant4.9.3/data/G4NDL3.13
On this machine the G4ABLADATA=/data/geant/geant4.9.3/data/G4ABLA3.0
On this machine the G4REALSURFACEDATA=/data/geant/geant4.9.3/data/RealSurface1.0
On this machine the CLHEP_BASE_DIR=/data/geant/CLHEP_2.0.4.5
On this machine the CLHEP_INCLUDE_DIR=/data/geant/CLHEP_2.0.4.5/include
On this machine the CLHEP_LIB_DIR=/data/geant/CLHEP_2.0.4.5/lib
On this machine the CLHEP_LIB=CLHEP
On this machine the G4UI_USE_TCSH=1
On this machine the G4VIS_BUILD_DAWN_DRIVER=1
On this machine the G4VIS_BUILD_OPENGLX_DRIVER=1
On this machine the G4VIS_BUILD_VRML_DRIVER=1
On this machine the G4VIS_USE_DAWN=1
On this machine the G4VIS_USE_OPENGLX=1
On this machine the G4VIS_USE_VRML=1
On this machine the XMFLAGS=
On this machine the XMLIBS=
On this machine the XMFLAGS=
On this machine the XAWFLAGS=
On this machine the XAWLIBS=
On this machine the G4LIB_BUILD_SHARED=1
On this machine the G4SYSTEM=Linux-g++
nobani@linux-ficd:~>

``` this is what happen when I try to join from the laptop to the desktop.
and the following happen in the opposite direction without any massages:
```
nobani@linux-ficd:~> ssh morad@192.168.1.2
**|**

```at the last step nothing appear or done

I am using KDE ,openSUSE11.2
your help will be appreciated.
Respectfully
Morad

---

### Post by v1ad on 2010-06-12
first of all is your data directory in root? you won't have permissions in that directory. basically make sure your permissions allow are read write. 

if the data folder is in the directory where u log in do.
scp -r nobani@192.168.1.3:./data/geant .


if none of this works, enter the directory and do pwd. post that here.

---

### Post by nobani on 2010-06-12
> **v1ad said:**
> first of all is your data directory in root? you won't have permissions in that directory. basically make sure your permissions allow are read write. 

if the data folder is in the directory where u log in do.
scp -r nobani@192.168.1.3:./data/geant .


if none of this works, enter the directory and do pwd. post that here.

yes, I have a full permissions to read and write,

see the following:
```

morad@linux-m9c6:~> ssh nobani@192.168.1.3
Password:                                 
Last login: Sat Jun 12 20:21:59 2010 from 192.168.1.2
Have a lot of fun...
On this machine the G4SYSTEM=Linux-g++
On this machine the G4INSTALL=/data/geant/geant4.9.3
On this machine the G4LIB=/data/geant/geant4.9.3/lib
On this machine the G4LEVELGAMMADATA=/data/geant/geant4.9.3/data/PhotonEvaporation2.0
On this machine the G4RADIOACTIVEDATA=/data/geant/geant4.9.3/data/RadioactiveDecay3.2
On this machine the G4LEDATA=/data/geant/geant4.9.3/data/G4EMLOW6.9
On this machine the G4NEUTRONHPDATA=/data/geant/geant4.9.3/data/G4NDL3.13
On this machine the G4ABLADATA=/data/geant/geant4.9.3/data/G4ABLA3.0
On this machine the G4REALSURFACEDATA=/data/geant/geant4.9.3/data/RealSurface1.0
On this machine the CLHEP_BASE_DIR=/data/geant/CLHEP_2.0.4.5
On this machine the CLHEP_INCLUDE_DIR=/data/geant/CLHEP_2.0.4.5/include
On this machine the CLHEP_LIB_DIR=/data/geant/CLHEP_2.0.4.5/lib
On this machine the CLHEP_LIB=CLHEP
On this machine the G4UI_USE_TCSH=1
On this machine the G4VIS_BUILD_DAWN_DRIVER=1
On this machine the G4VIS_BUILD_OPENGLX_DRIVER=1
On this machine the G4VIS_BUILD_VRML_DRIVER=1
On this machine the G4VIS_USE_DAWN=1
On this machine the G4VIS_USE_OPENGLX=1
On this machine the G4VIS_USE_VRML=1
On this machine the XMFLAGS=
On this machine the XMLIBS=
On this machine the XMFLAGS=
On this machine the XAWFLAGS=
On this machine the XAWLIBS=
On this machine the G4LIB_BUILD_SHARED=1
nobani@linux-ficd:~> cd /data
nobani@linux-ficd:/data> ls
geant  lost+found
nobani@linux-ficd:/data> cd geant/
nobani@linux-ficd:/data/geant> pwd
/data/geant
nobani@linux-ficd:/data/geant>

```
I want to transfere the geant folder from nobani to the /data at morad

---

