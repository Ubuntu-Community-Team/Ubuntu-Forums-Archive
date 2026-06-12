---
title: "K3B help please"
date: 2009-03-18
forum: Multimedia Software
---

### Post by Nadinesky on 2009-03-18
Hi I am fairly new to Ubuntu but have burned dvd's successfully before from ISO images.  My system was fully upgraded to Ubuntu fusion?? If that makes sense


When I start K3B and start burn, it burns 1% then my whole computer screen goes grayed out except K3B then it just says write error, no code or anything.

It does say:
Writing Mode Incremental Streaming Not available
Engaging DAO
Writing speed
Flushing Cache
Write Error

Below is the debugging report..,please help and remember keep it simple otherwise I am LOST! LOL

thanks in advance for the help

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-11-generic
Devices
-----------------------
SONY DVD RW DW-Q28A KYS1 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD-RW Sequential

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: FEATURE 21h is not on, engaging DAO...
/dev/scd0: reserving 312921 blocks
, warning for short DAO recording
/dev/scd0: "Current Write Speed" is 4.1x1352KBps.
      32768/640862208 ( 0.0%) @0.0x, remaining 977:49 RBU 100.0% UBU -100.0%
      32768/640862208 ( 0.0%) @0.0x, remaining 2281:35 RBU 100.0% UBU 100.0%
      32768/640862208 ( 0.0%) @0.0x, remaining 3259:25 RBU 100.0% UBU 100.0%
      32768/640862208 ( 0.0%) @0.0x, remaining 4237:15 RBU 100.0% UBU 100.0%
      32768/640862208 ( 0.0%) @0.0x, remaining 5541:01 RBU 100.0% UBU 100.0%
      32768/640862208 ( 0.0%) @0.0x, remaining 6518:51 RBU 100.0% UBU 100.0%
    1277952/640862208 ( 0.2%) @0.3x, remaining 191:50 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @1.8x, remaining 29:10 RBU 100.0% UBU  96.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 32:25 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 35:40 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 39:59 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 43:14 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 46:28 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 50:47 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 54:02 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 57:17 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 61:36 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 64:51 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 68:05 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 72:24 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=1290h failed with SK=2h/LOGICAL UNIT IS IN PROCESS OF BECOMING READY]: Resource temporarily unavailable
:-( write failed: Resource temporarily unavailable
/dev/scd0: flushing cache
:-[ FLUSH CACHE failed with SK=2h/LOGICAL UNIT IS IN PROCESS OF BECOMING READY]: Resource temporarily unavailable
    9732096/640862208 ( 1.5%) @0.0x, remaining 75:39 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 78:54 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 83:13 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 86:28 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 89:42 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 94:01 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 97:16 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 100:31 RBU 100.0% UBU 100.0%
    9732096/640862208 ( 1.5%) @0.0x, remaining 104:50 RBU 100.0% UBU 100.0%

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:312921 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m 

Just a lot of gibberish to me

thanks again
Nadine

---

