---
title: "Cannot burn CD's or DVD's"
date: 2011-12-16
forum: Multimedia Software
---

### Post by AbdRahim on 2011-12-16
Cannot burn DVD's with k3b.

Devices
-----------------------
Optiarc DVD RW AD-7260S 1.03 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.7.2 (4.7.2)
QT Version:  4.7.4
Kernel:      3.0.0-14-generic

Used versions
-----------------------
mkisofs: 1.1.11

mkisofs
-----------------------
/usr/bin/genisoimage: No such file or directory. Invalid node - '/home/xxx/.kde/share/apps/k3b/temp/'.

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid SPANISH LESSONS -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /home/xxx/.kde/tmp-ABC/k3bzm6729.tmp -rational-rock -hide-list /home/xxx/.kde/tmp-ABC/k3bKx6729.tmp -joliet -joliet-long -hide-joliet-list /home/xxx/.kde/tmp-ABC/k3bNA6729.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /home/xxx/.kde/tmp-ABC/k3beJ6729.tmp

Tried with Brasero and got coaster.

---

