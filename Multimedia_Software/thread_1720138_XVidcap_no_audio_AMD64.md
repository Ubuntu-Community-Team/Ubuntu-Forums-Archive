---
title: "XVidcap no audio AMD64"
date: 2011-04-02
forum: Multimedia Software
---

### Post by sderrick on 2011-04-02
I'm trying to get xVidcap to play nice with padsp in 10.10 AMD64

I  have seen [http://ubuntuforums.org/showpost.php?p=10607591](http://ubuntuforums.org/showpost.php?p=10607591)

Which works for i386 installations but there is no amd64 download of xvidcap on sourceforge.

So I downloaded the source for xvidcap but it fails because shmstr.h has been removed from x11proto-xext-dev as of Ubuntu 10.04!  I tried a desperate hack of just copying it into the correct directory but that blew up the build even worse!

So I downloaded the latest debian xvidcap_1.1.7-0.6_amd64.deb, but it depends on a new libavcodec52, version 6.1.  I tried to install that codec but the package manager says that conflicts with the current libavcodec52,version 5.something. so I uninstalled that which causes the package manager to install libavcodec-extra52,  which also conflicts with the newer codec??

WTF???

Anybody get this working?

---

### Post by sderrick on 2011-04-03
I found this [http://doc.ubuntu-fr.org/xvidcap](http://doc.ubuntu-fr.org/xvidcap)

An initial test shows success.  :D

Install package libavcodec-unstripped-51 instead of libavcodec51 . Normally libavcodec51 will uninstall automatically after installing libavcodec-unstripped-51 . For Jaunty , it's libavcodec-unstripped-52 to replace libavcodec52 .
Compile and install the version 1.1.7 . It is necessary to first install the packages libgtk2.0-dev , libglade2-dev , libxmu-dev and build-essential . Others may also be required. Then, unzip the downloaded archive, open a terminal, enter the directory xvidcap-1.1.7 / and run:
. / Configure make sudo make install
with Lucid Lynx

by doing: make, appears an error: capture.c: 68:35: error: X11/extensions/shmstr.h: No such file or folder of this type

edit the file: xvidcap-1.1.7/src/capture.c and replace the line

# Include <X11/extensions/shmstr.h>

by

# Include <X11/extensions/shmproto.h>

This is due to the version of the package x11-proto-dev-xext included in Lucid. Shmstr.h file is replaced with the file in the version of shmproto.h lucid.

---

