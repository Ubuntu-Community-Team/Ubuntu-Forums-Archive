---
title: "genisoimage not working kubuntu 10.10"
date: 2010-12-16
forum: Multimedia Software
---

### Post by mardukvmbc on 2010-12-16
I have this error anytime I use anything that needs genisoimage, like K9Copy or K3b. Same kind of error if I try to use genisoimage from the commandline:

```
Devices
-----------------------
ATAPI iHAS122   8 3L03 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

System
-----------------------
K3b Version: 2.0.1
KDE Version: 4.5.1 (KDE 4.5.1)
QT Version:  4.7.0
Kernel:      2.6.35-23-generic

Used versions
-----------------------
mkisofs: 1.1.10

mkisofs
-----------------------
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VTS info.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-jason/k3bVY4579.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-jason/k3bgs4579.tmp -dvd-video -f /tmp/kde-jason/k3bVideoDvd0
```

Any ideas?

---

