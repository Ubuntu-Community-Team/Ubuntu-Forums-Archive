---
title: "dvd fails to burn"
date: 2009-01-20
forum: Multimedia Software
---

### Post by marquee moon on 2009-01-20
Using xubuntu 8.04, I'm attempting to burn a video DVD for the first time. 

I have an .AVI file which I have converted to an .ISO file using DeVeDe.

However, DeVeDe did not successfully burn the ISO to disk, so I tried K3b 

Using K3b, I had a "failure to burn" error. The burn began, and then failed after a few seconds. When I put the DVD back into the drive, the computer recognised it as a dvd and played the first few seconds of the film, then stopped. 

The error file is below: 


System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-23-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-850S 1.10 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite]

Burned media
-----------------------
DVD+R

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 8.2x1352KBps.
    1572864/1969778688 ( 0.1%) @0.0x, remaining 125:08 RBU 100.0% UBU   2.1%
    1572864/1969778688 ( 0.1%) @0.0x, remaining 187:42 RBU 100.0% UBU 100.0%
    1572864/1969778688 ( 0.1%) @0.0x, remaining 250:16 RBU 100.0% UBU 100.0%
    1572864/1969778688 ( 0.1%) @0.0x, remaining 333:41 RBU 100.0% UBU 100.0%
    1572864/1969778688 ( 0.1%) @0.0x, remaining 396:15 RBU 100.0% UBU 100.0%
    1572864/1969778688 ( 0.1%) @0.0x, remaining 458:49 RBU 100.0% UBU 100.0%
    1572864/1969778688 ( 0.1%) @0.0x, remaining 542:15 RBU 100.0% UBU 100.0%
    2490368/1969778688 ( 0.1%) @0.2x, remaining 381:48 RBU 100.0% UBU  93.8%
    3112960/1969778688 ( 0.2%) @0.1x, remaining 336:56 RBU 100.0% UBU 100.0%
    3112960/1969778688 ( 0.2%) @0.0x, remaining 379:03 RBU 100.0% UBU 100.0%
    3112960/1969778688 ( 0.2%) @0.0x, remaining 410:38 RBU 100.0% UBU 100.0%
    3112960/1969778688 ( 0.2%) @0.0x, remaining 442:14 RBU 100.0% UBU 100.0%
    3112960/1969778688 ( 0.2%) @0.0x, remaining 484:21 RBU 100.0% UBU 100.0%
    3112960/1969778688 ( 0.2%) @0.0x, remaining 515:56 RBU 100.0% UBU 100.0%
    3112960/1969778688 ( 0.2%) @0.0x, remaining 547:31 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=5f0h failed with SK=3h/ASC=02h/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: closing track
/dev/scd0: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:961806 -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m

---

### Post by d3ngar on 2009-05-04
I have a similar problem, although mine seems to be related to Power Calibration:

```

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-11-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-860S 1.00 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 2145155 (4393277440 bytes)
Pipe throughput: 35180544 bytes read, 35176448 bytes written.

Used versions
-----------------------
mkisofs: 1.1.9
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 8.2x1352KBps.
    1572864/4393277440 ( 0.0%) @0.0x, remaining 279:13 RBU 100.0% UBU   2.1%
    1572864/4393277440 ( 0.0%) @0.0x, remaining 418:49 RBU 100.0% UBU 100.0%
    1572864/4393277440 ( 0.0%) @0.0x, remaining 604:58 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=300h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
:-( write failed: Input/output error
/dev/sr0: flushing cache
/dev/sr0: closing track
:-[ CLOSE TRACK failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
/dev/sr0: closing disc
:-[ CLOSE DISC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2145155 -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
2145155
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.02% done, estimate finish Mon May  4 16:20:41 2009
  0.05% done, estimate finish Mon May  4 15:45:37 2009
  0.07% done, estimate finish Mon May  4 15:33:31 2009
  0.09% done, estimate finish Mon May  4 15:27:41 2009
  0.12% done, estimate finish Mon May  4 15:24:10 2009
  0.14% done, estimate finish Mon May  4 15:21:48 2009
  0.16% done, estimate finish Mon May  4 15:20:04 2009
  0.19% done, estimate finish Mon May  4 15:18:49 2009
  0.21% done, estimate finish Mon May  4 15:17:50 2009
  0.23% done, estimate finish Mon May  4 15:17:02 2009
  0.26% done, estimate finish Mon May  4 15:16:23 2009
  0.28% done, estimate finish Mon May  4 15:15:50 2009
  0.30% done, estimate finish Mon May  4 15:15:23 2009
  0.33% done, estimate finish Mon May  4 15:15:00 2009
  0.35% done, estimate finish Mon May  4 15:14:39 2009
  0.37% done, estimate finish Mon May  4 15:14:21 2009
  0.40% done, estimate finish Mon May  4 15:14:06 2009
  0.42% done, estimate finish Mon May  4 15:13:52 2009
  0.44% done, estimate finish Mon May  4 15:13:39 2009
  0.47% done, estimate finish Mon May  4 15:13:28 2009
  0.49% done, estimate finish Mon May  4 15:13:18 2009
  0.51% done, estimate finish Mon May  4 15:13:08 2009
  0.54% done, estimate finish Mon May  4 15:13:00 2009
  0.56% done, estimate finish Mon May  4 15:12:52 2009
  0.58% done, estimate finish Mon May  4 15:12:45 2009
  0.61% done, estimate finish Mon May  4 15:12:38 2009
  0.63% done, estimate finish Mon May  4 15:12:32 2009
  0.65% done, estimate finish Mon May  4 15:12:27 2009
  0.68% done, estimate finish Mon May  4 15:12:21 2009
  0.70% done, estimate finish Mon May  4 15:12:17 2009
  0.72% done, estimate finish Mon May  4 15:12:12 2009
  0.75% done, estimate finish Mon May  4 15:12:07 2009
  0.77% done, estimate finish Mon May  4 15:12:03 2009
  0.79% done, estimate finish Mon May  4 15:12:00 2009

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid The.Pink.Panther.BOXSET.DVDRip -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-dengar/k3bbZFkrb.tmp -rational-rock -hide-list /tmp/kde-dengar/k3bND8mtc.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-dengar/k3b1Mnm3a.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-dengar/k3bvvMxgb.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid The.Pink.Panther.BOXSET.DVDRip -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-dengar/k3bj8tSZb.tmp -rational-rock -hide-list /tmp/kde-dengar/k3bhkay3a.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-dengar/k3bazYyra.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-dengar/k3bh2RTta.tmp 

```

I don't know what to do. I read that this could be related to the Media not being in good quality or incompatible with my MATSHITA DVD-RAM UJ-860S. These were Sony DVD-R, but I have tried some Verbatim DVD+R and they didn't burn either.

In any way, the burn process doesn't start, so I don't actually lose a DVD when I try, but it's quite annoying.

Now the problem is that the burner used to work fine and I was able to burn DVDs under Gutsy, until recently. I thought that a complete reinstall of my machine, going to Jaunty would fix the problems, but no :(

Any advise appreciated.

---

### Post by drkitty on 2009-07-17
I'm bumping this.  I can burn a couple of dvds, then brasero spits out:
 "0h failed with SK=3h/POWER CALIBRATION AREA ERROR"  Seems like IO is not getting released.  Help appreciated.

---

