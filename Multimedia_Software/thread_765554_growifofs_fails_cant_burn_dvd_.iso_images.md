---
title: "growifofs fails cant burn dvd .iso images"
date: 2008-04-24
forum: Multimedia Software
---

### Post by jza873 on 2008-04-24
hay i usually dont post but i ran into one hell of a problem.  well everything was working fine then i did a dist-upgrade and all of the sudden i cant burn and .iso to a dvd.  here is the error:


System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-16-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-85JS F100 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 2.5x1352KBps.
    1572864/759803904 ( 0.2%) @0.3x, remaining 40:10 RBU 100.0% UBU   2.1%
    1572864/759803904 ( 0.2%) @0.0x, remaining 64:16 RBU 100.0% UBU 100.0%
    1572864/759803904 ( 0.2%) @0.0x, remaining 96:24 RBU 100.0% UBU 100.0%
    1572864/759803904 ( 0.2%) @0.0x, remaining 120:31 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=300h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: closing track
:-[ CLOSE TRACK failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
/dev/scd0: closing disc
:-[ CLOSE DISC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error

growisofs command:
-----------------------
/usr/X11R6/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:370998 -dvd-compat -speed=2.4 -overburn -use-the-force-luke=bufsize:32m 

this happened to be b4 when i upgraded to 7.10 ended up buring the distro like 3 times then finally it worked.  hay i see this all over the net and no one can figure out what its about or how to fix it.  any help will be great

---

