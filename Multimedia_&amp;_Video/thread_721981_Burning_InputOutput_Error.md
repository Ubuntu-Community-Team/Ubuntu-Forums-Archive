---
title: "Burning Input/Output Error"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by tessmonsta on 2008-03-11
I'm trying to burn some data DVDs and I'm having no luck at all. K3b always seems to error out. I managed one disc, but the rest return an error similar to below:

```
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
SONY DVD RW DW-Q58A UFS2 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 1060927 (2172778496 bytes)
Pipe throughput: 33671168 bytes read, 33650688 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 6.1x1352KBps.
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2172778496 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1060927 -dvd-compat -speed=6 -overburn -use-the-force-luke=bufsize:700m 

mkisofs
-----------------------
1060927
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.05% done, estimate finish Tue Mar 11 22:03:37 2008
  0.09% done, estimate finish Tue Mar 11 22:03:37 2008
  0.14% done, estimate finish Tue Mar 11 22:15:22 2008
  0.19% done, estimate finish Tue Mar 11 22:12:23 2008
  0.24% done, estimate finish Tue Mar 11 22:10:39 2008
  0.28% done, estimate finish Tue Mar 11 22:09:29 2008
  0.33% done, estimate finish Tue Mar 11 22:08:39 2008
  0.38% done, estimate finish Tue Mar 11 22:08:01 2008
  0.43% done, estimate finish Tue Mar 11 22:07:32 2008
  0.47% done, estimate finish Tue Mar 11 22:07:08 2008
  0.52% done, estimate finish Tue Mar 11 22:06:49 2008
  0.57% done, estimate finish Tue Mar 11 22:06:33 2008
  0.61% done, estimate finish Tue Mar 11 22:06:19 2008
  0.66% done, estimate finish Tue Mar 11 22:06:08 2008
  0.71% done, estimate finish Tue Mar 11 22:05:58 2008
  0.76% done, estimate finish Tue Mar 11 22:05:49 2008
  0.80% done, estimate finish Tue Mar 11 22:05:41 2008
  0.85% done, estimate finish Tue Mar 11 22:05:34 2008
  0.90% done, estimate finish Tue Mar 11 22:05:28 2008
  0.94% done, estimate finish Tue Mar 11 22:05:22 2008
  0.99% done, estimate finish Tue Mar 11 22:05:17 2008
  1.04% done, estimate finish Tue Mar 11 22:06:49 2008
  1.08% done, estimate finish Tue Mar 11 22:06:41 2008
  1.13% done, estimate finish Tue Mar 11 22:06:33 2008
  1.18% done, estimate finish Tue Mar 11 22:06:26 2008
  1.23% done, estimate finish Tue Mar 11 22:06:20 2008
  1.27% done, estimate finish Tue Mar 11 22:06:14 2008
  1.32% done, estimate finish Tue Mar 11 22:06:08 2008
  1.37% done, estimate finish Tue Mar 11 22:06:03 2008
  1.41% done, estimate finish Tue Mar 11 22:07:09 2008
  1.46% done, estimate finish Tue Mar 11 22:07:02 2008
  1.51% done, estimate finish Tue Mar 11 22:06:55 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Texhnolyze_12-22 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-tess/k3bwcZT7b.tmp -rational-rock -hide-list /tmp/kde-tess/k3bG7UdLb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-tess/k3bO7xyHb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-tess/k3bcDTync.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Texhnolyze_12-22 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-tess/k3b88bdYb.tmp -rational-rock -hide-list /tmp/kde-tess/k3bzC6zwb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-tess/k3bFkgprb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-tess/k3boSLIJa.tmp
```

---

### Post by tessmonsta on 2008-03-12
Cancel that, everyone is having this issue right now. I should have checked more throughly before posting.... >_<

---

