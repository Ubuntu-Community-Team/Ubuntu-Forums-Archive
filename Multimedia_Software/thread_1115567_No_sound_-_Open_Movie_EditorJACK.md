---
title: "No sound - Open Movie Editor/JACK"
date: 2009-04-04
forum: Multimedia Software
---

### Post by aggitan on 2009-04-04
Request for support:
 I'm not sure if this is an issue with the way I'm connecting my plugs within JACK or if it is a problem with Open Movie Editor. 

OME says it is able to connect just fine, or rather it doesn't say that it is not able to connect.
I do not get any sound either before render during preview or after render. I use VLC

System Details
```
aggitan@Moneque:~$ uname -a
Linux Moneque 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Li
```
JACK Details:
--Startup Information
```
aggitan@Moneque:~$ qjackctl
Warning: no locale found: /usr/share/locale/qjackctl_en_US.qm
```
--About Information
```
JACK Audio Connection Kit - Qt GUI Interface

Version: 0.3.2
Build: Feb 8 2008 04:48:37
```
Open Movie Editor Details
```
Open Movie Editor
0.0.20080102
```
Supporting Information

Open Movie Editor Startup Details
```
aggitan@Moneque:~$ openmovieeditor 
When submitting a BUG report, or SUPPORT request, please include the following information:
----8<-----------------------
Libquicktime Version: 1.0.2
Libquicktime API Version: 9
libavcodec Version: Lavc51.50.0
libavformat Version: Lavf52.7.0
/etc/debian_version:
lenny/sid
/etc/lsb-release:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
----8<-----------------------
Jack Samplerate: 48000
mdb:511, lastbuf:0 skipping granule 0
mdb:511, lastbuf:0 skipping granule 0
mdb:511, lastbuf:0 skipping granule 1
mdb:511, lastbuf:0 skipping granule 1
mdb:511, lastbuf:0 skipping granule 0
mdb:511, lastbuf:0 skipping granule 0
mdb:511, lastbuf:0 skipping granule 1
mdb:511, lastbuf:0 skipping granule 1
mdb:136, lastbuf:0 skipping granule 0
mdb:136, lastbuf:0 skipping granule 0
mdb:136, lastbuf:0 skipping granule 1
mdb:136, lastbuf:0 skipping granule 1
mdb:48, lastbuf:0 skipping granule 0
mdb:43, lastbuf:0 skipping granule 0
mdb:179, lastbuf:0 skipping granule 0
mdb:47, lastbuf:0 skipping granule 0
mdb:19, lastbuf:0 skipping granule 0
mdb:136, lastbuf:0 skipping granule 0
mdb:136, lastbuf:0 skipping granule 0
mdb:136, lastbuf:0 skipping granule 1
mdb:136, lastbuf:0 skipping granule 1
When submitting a BUG report, or SUPPORT request, please include the following information:
----8<-----------------------
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3850
OpenGL version string: 2.1.8087 Release
GL_MAX_TEXTURE_SIZE = 8192
----8<-----------------------
```
--Large Screen-Shot
[http://novaa.net/Screenshot-2.png](http://novaa.net/Screenshot-2.png)

--Hardware Specifics 
[http://novaa.net/hardwaredetails.html](http://novaa.net/hardwaredetails.html)



______
Thank you for your time

---

