---
title: "K3B/growisofs no longer works after going to Edgy"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by TomG on 2007-02-06
Hi 

I upgraded to Edgy a few days ago and now I desperately try to format/burn a DVD+RW with K3B. It fails systematically and the output log show :

[I]System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-386
Devices
-----------------------
PIONEER DVD-RW  DVR-108 1.10 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

K3b
-----------------------
Size of filesystem calculated: 3958916

Used versions
-----------------------
growisofs: 6.1

[B]growisofs
-----------------------
WARNING: /dev/hdc already carries isofs!
About to execute 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
:-( /dev/hdc: 2295104 blocks are free, 3958916 to be written![/B]

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:3958916 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
....[/I]

The growisofs command ("/usr/bin/X11/growisofs -Z /dev/hdc=/dev/fd/0... ") always fails. I tried to downgrade DVD+RW-tools to 6.0 but I got the same result;
I've found a few information over the net but nothing intersting.
Any idea please ? :confused: 

Thanks
TomG

---

### Post by TomG on 2007-02-07
Bump :(

---

### Post by Gen2ly on 2007-07-06
There's a previous filesystem on the CD.  The best way to that is to erase the data:

> growisofs -Z /dev/dvd=/dev/zero

good luck.

---

