---
title: "Can not Burn DVD - K3B and Brasero"
date: 2009-11-27
forum: Multimedia Software
---

### Post by woody22075 on 2009-11-27
I am running Intrepid and can not burn a dvd.  I receive an input/output error when attempting to use either Brasero or K3B to burn.  Below is the error output from K3B.  I used to be able to burn under 8.04.  Any suggestions as to the problem and how I might fix?

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-11-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-T20L NC08 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 959677 (1965418496 bytes)
Pipe throughput: 34762752 bytes read, 34758272 bytes written.

Used versions
-----------------------
mkisofs: 1.1.8
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 4.1x1352KBps.
    1114112/1965418496 ( 0.1%) @0.0x, remaining 146:55 RBU 100.0% UBU   2.9%
    1114112/1965418496 ( 0.1%) @0.0x, remaining 264:28 RBU 100.0% UBU 100.0%
    1114112/1965418496 ( 0.1%) @0.0x, remaining 352:37 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=220h failed with SK=3h/WRITE ERROR]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=A0h/ACQ=80h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:959677 -speed=4 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
959677
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.05% done, estimate finish Fri Nov 27 10:49:03 2009
  0.11% done, estimate finish Fri Nov 27 10:49:03 2009
  0.16% done, estimate finish Fri Nov 27 10:49:03 2009
  0.21% done, estimate finish Fri Nov 27 10:49:03 2009
  0.26% done, estimate finish Fri Nov 27 10:49:03 2009
  0.31% done, estimate finish Fri Nov 27 10:49:03 2009
  0.37% done, estimate finish Fri Nov 27 10:49:03 2009
  0.42% done, estimate finish Fri Nov 27 10:49:03 2009
  0.47% done, estimate finish Fri Nov 27 10:49:03 2009
  0.52% done, estimate finish Fri Nov 27 10:49:03 2009
  0.57% done, estimate finish Fri Nov 27 10:49:03 2009
  0.63% done, estimate finish Fri Nov 27 10:49:03 2009
  0.68% done, estimate finish Fri Nov 27 10:49:03 2009
  0.73% done, estimate finish Fri Nov 27 10:49:03 2009
  0.78% done, estimate finish Fri Nov 27 10:49:03 2009
  0.83% done, estimate finish Fri Nov 27 10:49:03 2009
  0.89% done, estimate finish Fri Nov 27 10:49:03 2009
  0.94% done, estimate finish Fri Nov 27 10:49:03 2009
  0.99% done, estimate finish Fri Nov 27 10:49:03 2009
  1.04% done, estimate finish Fri Nov 27 10:49:03 2009
  1.10% done, estimate finish Fri Nov 27 10:49:03 2009
  1.15% done, estimate finish Fri Nov 27 10:49:03 2009
  1.20% done, estimate finish Fri Nov 27 10:49:03 2009
  1.25% done, estimate finish Fri Nov 27 10:49:03 2009
  1.30% done, estimate finish Fri Nov 27 10:49:03 2009
  1.36% done, estimate finish Fri Nov 27 10:49:03 2009
  1.41% done, estimate finish Fri Nov 27 10:50:14 2009
  1.46% done, estimate finish Fri Nov 27 10:50:11 2009
  1.51% done, estimate finish Fri Nov 27 10:50:09 2009
  1.56% done, estimate finish Fri Nov 27 10:50:06 2009
  1.62% done, estimate finish Fri Nov 27 10:50:04 2009
  1.67% done, estimate finish Fri Nov 27 10:50:02 2009
  1.72% done, estimate finish Fri Nov 27 10:50:01 2009
  1.77% done, estimate finish Fri Nov 27 10:49:59 2009

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid that mitchell and webb look -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-marshallVOQJeZ/k3bvM1v6a.tmp -rational-rock -hide-list /tmp/kde-marshallVOQJeZ/k3b4yJWFb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-marshallVOQJeZ/k3bHFF8ab.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-marshallVOQJeZ/k3bLkasga.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid that mitchell and webb look -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-marshallVOQJeZ/k3bY3UCbc.tmp -rational-rock -hide-list /tmp/kde-marshallVOQJeZ/k3b1WnFkc.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-marshallVOQJeZ/k3b2Xa4Ea.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-marshallVOQJeZ/k3bGnDoQb.tmp

---

