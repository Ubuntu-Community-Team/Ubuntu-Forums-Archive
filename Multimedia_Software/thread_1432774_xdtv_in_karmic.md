---
title: "xdtv in karmic"
date: 2010-03-18
forum: Multimedia Software
---

### Post by johnaaronrose on 2010-03-18
I'm trying to install xdtv on karmic as shown below (from an old read-only thread on installing it in gutsy):
 
 1- Install XDTV from xdtv web site ( deb package ) - OK
 2- Install libxdtv from xdtv web site ( deb package ) - OK
 3- Need libXaw3d.so.6: Parts in this package:
 sudo apt-get install xaw3dg - OK
 4- Install libzvbi.so.0 from repos ( libzvbi in Synaptic ) - actually libzvbi0 in Synaptic
 
 Opening xdtv from the terminal gives:
xdtv: error while loading shared libraries: libneXtaw.so.0: cannot open shared object file: No such file or directory

There seems to be file of that name on PC. There seems to be no package of that or similar name (e.g. nextaw) in Synaptic. 

I also tried installing tv-fonts (deb package) from xdtv web site but that was no help.

Any ideas?

---

### Post by L_V on 2010-05-27
At least available here:
[http://www.debian-multimedia.org/dists/stable/main/binary-i386/package/libnextaw0.php](http://www.debian-multimedia.org/dists/stable/main/binary-i386/package/libnextaw0.php)

---

