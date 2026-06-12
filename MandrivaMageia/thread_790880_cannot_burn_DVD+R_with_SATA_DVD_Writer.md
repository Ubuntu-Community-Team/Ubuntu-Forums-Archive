---
title: "cannot burn DVD+R with SATA DVD Writer"
date: 2008-05-11
forum: Mandriva/Mageia
---

### Post by &amp;wP*!) on 2008-05-11
Hi,

I am an Ubuntu user since 6.10 Edgy Eft. I recently installed 8.04 Hardy Heron, tried to burn a 16x DVD+R on a new SATA DVD Writer, LG GH20NS10. It did not go. To see, whether it has to do with the operating system itself, I have downloaded Mandriva 2008 Spring and installed it.

I have run K3B and I still get the same error. Please see the attached file to see K3B error window.

This DVD+R can be burned with this SATA DVD Writer **without any problem on Windows XP**.

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24.4-desktop-1mnb
Devices
-----------------------
HL-DT-ST DVDRAM GH20NS10 EL00 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

SAMSUNG CDRW/DVD SM-352B T809 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]
Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 1937608 (3968221184 bytes)
Pipe throughput: 1655496704 bytes read, 1655476224 bytes written.

Used versions
-----------------------
mkisofs: 1.1.7.1
growisofs: 7.0

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 16.4x1352KBps.
          0/3968221184 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3968221184 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3968221184 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3968221184 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3968221184 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3968221184 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
    1114112/3968221184 ( 0.0%) @0.2x, remaining 1483:39 RBU 100.0% UBU   2.9%
   25788416/3968221184 ( 0.6%) @5.3x, remaining 71:20 RBU 100.0% UBU 100.0%
   59146240/3968221184 ( 1.5%) @7.2x, remaining 35:14 RBU 100.0% UBU 100.0%
   93093888/3968221184 ( 2.3%) @7.4x, remaining 24:16 RBU 100.0% UBU 100.0%
  127565824/3968221184 ( 3.2%) @7.5x, remaining 19:04 RBU 100.0% UBU 100.0%
  162594816/3968221184 ( 4.1%) @7.6x, remaining 16:23 RBU 100.0% UBU 100.0%
  198180864/3968221184 ( 5.0%) @7.7x, remaining 14:16 RBU 100.0% UBU 100.0%
  234323968/3968221184 ( 5.9%) @7.8x, remaining 12:44 RBU 100.0% UBU 100.0%
  270991360/3968221184 ( 6.8%) @7.9x, remaining 11:49 RBU 100.0% UBU 100.0%
  304250880/3968221184 ( 7.7%) @7.2x, remaining 11:02 RBU 100.0% UBU 100.0%
  341999616/3968221184 ( 8.6%) @8.2x, remaining 10:14 RBU 100.0% UBU 100.0%
  380272640/3968221184 ( 9.6%) @8.3x, remaining 9:44 RBU 100.0% UBU 100.0%
  419135488/3968221184 (10.6%) @8.4x, remaining 9:10 RBU 100.0% UBU 100.0%
  458522624/3968221184 (11.6%) @8.5x, remaining 8:40 RBU 100.0% UBU  97.1%
  498466816/3968221184 (12.6%) @8.7x, remaining 8:21 RBU 100.0% UBU 100.0%
  538935296/3968221184 (13.6%) @8.8x, remaining 7:57 RBU 100.0% UBU 100.0%
  579993600/3968221184 (14.6%) @8.9x, remaining 7:35 RBU 100.0% UBU  97.1%
  621576192/3968221184 (15.7%) @9.0x, remaining 7:21 RBU 100.0% UBU  97.1%
  663748608/3968221184 (16.7%) @9.1x, remaining 7:03 RBU 100.0% UBU  97.1%
  706445312/3968221184 (17.8%) @9.3x, remaining 6:46 RBU 100.0% UBU 100.0%
  749699072/3968221184 (18.9%) @9.4x, remaining 6:34 RBU 100.0% UBU 100.0%
  793509888/3968221184 (20.0%) @9.5x, remaining 6:20 RBU 100.0% UBU 100.0%
  837877760/3968221184 (21.1%) @9.6x, remaining 6:06 RBU 100.0% UBU 100.0%
  882769920/3968221184 (22.2%) @9.7x, remaining 5:56 RBU 100.0% UBU 100.0%
  928251904/3968221184 (23.4%) @9.9x, remaining 5:43 RBU 100.0% UBU 100.0%
  974258176/3968221184 (24.6%) @10.0x, remaining 5:31 RBU 100.0% UBU 100.0%
 1015971840/3968221184 (25.6%) @9.0x, remaining 5:25 RBU 100.0% UBU  97.1%
 1063026688/3968221184 (26.8%) @10.2x, remaining 5:14 RBU 100.0% UBU 100.0%
 1110638592/3968221184 (28.0%) @10.3x, remaining 5:03 RBU 100.0% UBU 100.0%
 1158807552/3968221184 (29.2%) @10.4x, remaining 4:55 RBU 100.0% UBU  97.1%
 1207533568/3968221184 (30.4%) @10.6x, remaining 4:45 RBU 100.0% UBU 100.0%
 1256816640/3968221184 (31.7%) @10.7x, remaining 4:36 RBU 100.0% UBU  97.1%
 1306656768/3968221184 (32.9%) @10.8x, remaining 4:28 RBU  99.9% UBU 100.0%
 1357053952/3968221184 (34.2%) @10.9x, remaining 4:19 RBU 100.0% UBU 100.0%
 1407975424/3968221184 (35.5%) @11.0x, remaining 4:10 RBU 100.0% UBU 100.0%
 1459453952/3968221184 (36.8%) @11.2x, remaining 4:04 RBU 100.0% UBU 100.0%
 1511489536/3968221184 (38.1%) @11.3x, remaining 3:55 RBU 100.0% UBU 100.0%
 1564082176/3968221184 (39.4%) @11.4x, remaining 3:47 RBU  98.6% UBU 100.0%
 1617231872/3968221184 (40.8%) @11.5x, remaining 3:40 RBU  99.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @1.0x, remaining 3:44 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 3:48 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 3:54 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 3:58 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:03 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:08 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:13 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:17 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:23 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:27 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:31 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:37 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:42 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:46 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:52 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 4:56 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 5:00 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 5:06 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 5:11 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 5:15 RBU 100.0% UBU 100.0%
 1621819392/3968221184 (40.9%) @0.0x, remaining 5:21 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=c1560h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( write failed: Input/output error
/dev/sr0: flushing cache
/dev/sr0: closing track
/dev/sr0: closing session

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1937608 -speed=16 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
1937608
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using ... (some filenames which I don't want to show to public)
  0.08% done, estimate finish Sun May 11 23:46:49 2008
  0.10% done, estimate finish Mon May 12 00:02:53 2008
  0.13% done, estimate finish Sun May 11 23:59:43 2008
  0.16% done, estimate finish Sun May 11 23:57:33 2008
  0.18% done, estimate finish Sun May 11 23:56:01 2008
  0.21% done, estimate finish Sun May 11 23:54:52 2008
  0.23% done, estimate finish Sun May 11 23:53:58 2008
  0.26% done, estimate finish Sun May 11 23:53:15 2008
  0.28% done, estimate finish Sun May 11 23:52:40 2008
  0.31% done, estimate finish Sun May 11 23:52:11 2008
  0.34% done, estimate finish Sun May 11 23:51:46 2008
  0.36% done, estimate finish Sun May 11 23:51:25 2008
  0.39% done, estimate finish Sun May 11 23:55:25 2008
  0.41% done, estimate finish Sun May 11 23:54:53 2008
  0.44% done, estimate finish Sun May 11 23:54:24 2008
  0.46% done, estimate finish Sun May 11 23:53:59 2008
  0.49% done, estimate finish Sun May 11 23:53:36 2008
  0.52% done, estimate finish Sun May 11 23:53:16 2008
  0.54% done, estimate finish Sun May 11 23:52:57 2008
  0.57% done, estimate finish Sun May 11 23:52:40 2008
  0.59% done, estimate finish Sun May 11 23:52:25 2008
  0.62% done, estimate finish Sun May 11 23:52:11 2008
  0.65% done, estimate finish Sun May 11 23:51:58 2008
  0.67% done, estimate finish Sun May 11 23:51:47 2008
  0.70% done, estimate finish Sun May 11 23:51:36 2008
  0.72% done, estimate finish Sun May 11 23:51:25 2008
  0.75% done, estimate finish Sun May 11 23:51:16 2008
  0.77% done, estimate finish Sun May 11 23:51:07 2008
  0.80% done, estimate finish Sun May 11 23:50:58 2008
  0.83% done, estimate finish Sun May 11 23:50:51 2008
  0.85% done, estimate finish Mon May 12 00:33:46 2008
  0.88% done, estimate finish Mon May 12 00:32:22 2008
  0.90% done, estimate finish Mon May 12 00:38:27 2008
  0.93% done, estimate finish Mon May 12 00:37:01 2008
  0.95% done, estimate finish Mon May 12 00:35:41 2008
  0.98% done, estimate finish Mon May 12 00:34:22 2008
  1.01% done, estimate finish Mon May 12 00:33:09 2008
  1.03% done, estimate finish Mon May 12 00:32:00 2008
  1.06% done, estimate finish Mon May 12 00:30:55 2008
  1.08% done, estimate finish Mon May 12 00:31:22 2008
  1.11% done, estimate finish Mon May 12 00:30:21 2008
  1.14% done, estimate finish Mon May 12 00:29:22 2008
  1.16% done, estimate finish Mon May 12 00:28:25 2008
  1.19% done, estimate finish Mon May 12 00:27:31 2008
  1.21% done, estimate finish Mon May 12 00:26:38 2008
  1.24% done, estimate finish Mon May 12 00:25:49 2008
  1.26% done, estimate finish Mon May 12 00:25:01 2008
  1.29% done, estimate finish Mon May 12 00:24:16 2008
  1.32% done, estimate finish Mon May 12 00:23:31 2008
  1.34% done, estimate finish Mon May 12 00:24:03 2008
  1.37% done, estimate finish Mon May 12 00:23:22 2008
  1.39% done, estimate finish Mon May 12 00:22:41 2008
  1.42% done, estimate finish Mon May 12 00:22:01 2008
  1.45% done, estimate finish Mon May 12 00:21:24 2008
  1.47% done, estimate finish Mon May 12 00:20:48 2008
  1.50% done, estimate finish Mon May 12 00:20:13 2008
  1.52% done, estimate finish Mon May 12 00:19:38 2008
  1.55% done, estimate finish Mon May 12 00:19:05 2008
  1.57% done, estimate finish Mon May 12 00:18:34 2008
  1.60% done, estimate finish Mon May 12 00:19:06 2008
  1.63% done, estimate finish Mon May 12 00:18:35 2008
  1.65% done, estimate finish Mon May 12 00:18:05 2008
  1.68% done, estimate finish Mon May 12 00:17:36 2008
  1.70% done, estimate finish Mon May 12 00:17:09 2008
  1.73% done, estimate finish Mon May 12 00:16:41 2008
  1.76% done, estimate finish Mon May 12 00:16:15 2008
  1.78% done, estimate finish Mon May 12 00:15:49 2008
  1.81% done, estimate finish Mon May 12 00:15:25 2008
  1.83% done, estimate finish Mon May 12 00:15:54 2008
  1.86% done, estimate finish Mon May 12 00:15:30 2008
  1.88% done, estimate finish Mon May 12 00:15:07 2008
  1.91% done, estimate finish Mon May 12 00:14:44 2008
  1.94% done, estimate finish Mon May 12 00:14:21 2008
  1.96% done, estimate finish Mon May 12 00:14:00 2008
  1.99% done, estimate finish Mon May 12 00:13:39 2008
  2.01% done, estimate finish Mon May 12 00:13:18 2008
  2.04% done, estimate finish Mon May 12 00:12:58 2008
  2.06% done, estimate finish Mon May 12 00:12:38 2008
  2.09% done, estimate finish Mon May 12 00:13:07 2008
  2.12% done, estimate finish Mon May 12 00:12:48 2008
  2.14% done, estimate finish Mon May 12 00:12:29 2008
  2.17% done, estimate finish Mon May 12 00:12:11 2008
  2.19% done, estimate finish Mon May 12 00:11:53 2008
  2.22% done, estimate finish Mon May 12 00:11:35 2008
  2.25% done, estimate finish Mon May 12 00:11:18 2008
  2.27% done, estimate finish Mon May 12 00:11:01 2008
  2.30% done, estimate finish Mon May 12 00:10:45 2008
  2.32% done, estimate finish Mon May 12 00:10:29 2008
  2.35% done, estimate finish Mon May 12 00:10:56 2008
  2.37% done, estimate finish Mon May 12 00:10:40 2008
  2.40% done, estimate finish Mon May 12 00:10:25 2008
  2.43% done, estimate finish Mon May 12 00:10:10 2008
  2.45% done, estimate finish Mon May 12 00:09:55 2008
  2.48% done, estimate finish Mon May 12 00:09:41 2008
  2.50% done, estimate finish Mon May 12 00:09:27 2008
  2.53% done, estimate finish Mon May 12 00:09:13 2008
  2.56% done, estimate finish Mon May 12 00:08:59 2008
  2.58% done, estimate finish Mon May 12 00:08:46 2008
  2.61% done, estimate finish Mon May 12 00:09:11 2008
  2.63% done, estimate finish Mon May 12 00:08:58 2008
  2.66% done, estimate finish Mon May 12 00:08:45 2008
  2.68% done, estimate finish Mon May 12 00:08:32 2008
  2.71% done, estimate finish Mon May 12 00:08:20 2008
  2.74% done, estimate finish Mon May 12 00:08:08 2008
  2.76% done, estimate finish Mon May 12 00:07:56 2008
  2.79% done, estimate finish Mon May 12 00:07:44 2008
  2.81% done, estimate finish Mon May 12 00:07:33 2008
  2.84% done, estimate finish Mon May 12 00:07:21 2008
  2.87% done, estimate finish Mon May 12 00:07:45 2008
  2.89% done, estimate finish Mon May 12 00:07:34 2008
  2.92% done, estimate finish Mon May 12 00:07:23 2008
  2.94% done, estimate finish Mon May 12 00:07:12 2008
  2.97% done, estimate finish Mon May 12 00:07:01 2008
  2.99% done, estimate finish Mon May 12 00:06:51 2008
  3.02% done, estimate finish Mon May 12 00:06:41 2008
  3.05% done, estimate finish Mon May 12 00:06:31 2008
  3.07% done, estimate finish Mon May 12 00:06:21 2008
  3.10% done, estimate finish Mon May 12 00:06:11 2008
  3.12% done, estimate finish Mon May 12 00:06:33 2008
  3.15% done, estimate finish Mon May 12 00:06:24 2008
  3.17% done, estimate finish Mon May 12 00:06:14 2008
  3.20% done, estimate finish Mon May 12 00:06:05 2008
  3.23% done, estimate finish Mon May 12 00:05:56 2008
  3.25% done, estimate finish Mon May 12 00:05:46 2008
  3.28% done, estimate finish Mon May 12 00:05:37 2008
  3.30% done, estimate finish Mon May 12 00:05:29 2008
  3.33% done, estimate finish Mon May 12 00:05:20 2008
  3.36% done, estimate finish Mon May 12 00:05:11 2008
  3.38% done, estimate finish Mon May 12 00:05:32 2008
  3.41% done, estimate finish Mon May 12 00:05:24 2008
  3.43% done, estimate finish Mon May 12 00:05:16 2008
  3.46% done, estimate finish Mon May 12 00:05:07 2008
  3.48% done, estimate finish Mon May 12 00:04:59 2008
  3.51% done, estimate finish Mon May 12 00:04:51 2008
  3.54% done, estimate finish Mon May 12 00:04:43 2008
  3.56% done, estimate finish Mon May 12 00:04:35 2008
  3.59% done, estimate finish Mon May 12 00:04:28 2008
  3.61% done, estimate finish Mon May 12 00:04:20 2008
  3.64% done, estimate finish Mon May 12 00:04:40 2008
  3.66% done, estimate finish Mon May 12 00:04:33 2008
  3.69% done, estimate finish Mon May 12 00:04:25 2008
  3.72% done, estimate finish Mon May 12 00:04:18 2008
  3.74% done, estimate finish Mon May 12 00:04:11 2008
  3.77% done, estimate finish Mon May 12 00:04:03 2008
  3.79% done, estimate finish Mon May 12 00:03:56 2008
  3.82% done, estimate finish Mon May 12 00:03:50 2008
  3.84% done, estimate finish Mon May 12 00:03:43 2008
  3.87% done, estimate finish Mon May 12 00:03:36 2008
  3.90% done, estimate finish Mon May 12 00:03:55 2008
  3.92% done, estimate finish Mon May 12 00:03:48 2008
  3.95% done, estimate finish Mon May 12 00:03:42 2008
  3.97% done, estimate finish Mon May 12 00:03:35 2008
  4.00% done, estimate finish Mon May 12 00:03:28 2008
  4.03% done, estimate finish Mon May 12 00:03:22 2008
  4.05% done, estimate finish Mon May 12 00:03:16 2008
  4.08% done, estimate finish Mon May 12 00:03:09 2008
  4.10% done, estimate finish Mon May 12 00:03:03 2008
  4.13% done, estimate finish Mon May 12 00:02:57 2008
  4.15% done, estimate finish Mon May 12 00:03:15 2008
  4.18% done, estimate finish Mon May 12 00:03:09 2008
  4.21% done, estimate finish Mon May 12 00:03:03 2008
  4.23% done, estimate finish Mon May 12 00:02:57 2008
  4.26% done, estimate finish Mon May 12 00:02:51 2008
  4.28% done, estimate finish Mon May 12 00:02:45 2008
  4.31% done, estimate finish Mon May 12 00:02:40 2008
  4.34% done, estimate finish Mon May 12 00:02:34 2008
  4.36% done, estimate finish Mon May 12 00:02:29 2008
  4.39% done, estimate finish Mon May 12 00:02:23 2008
  4.41% done, estimate finish Mon May 12 00:02:40 2008
  4.44% done, estimate finish Mon May 12 00:02:35 2008
  4.46% done, estimate finish Mon May 12 00:02:29 2008
  4.49% done, estimate finish Mon May 12 00:02:24 2008
  4.52% done, estimate finish Mon May 12 00:02:18 2008
  4.54% done, estimate finish Mon May 12 00:02:13 2008
  4.57% done, estimate finish Mon May 12 00:02:08 2008
  4.59% done, estimate finish Mon May 12 00:02:03 2008
  4.62% done, estimate finish Mon May 12 00:01:58 2008
  4.65% done, estimate finish Mon May 12 00:01:53 2008
  4.67% done, estimate finish Mon May 12 00:01:48 2008
  4.70% done, estimate finish Mon May 12 00:02:04 2008
  4.72% done, estimate finish Mon May 12 00:01:59 2008
  4.75% done, estimate finish Mon May 12 00:01:54 2008
  4.77% done, estimate finish Mon May 12 00:01:49 2008
  4.80% done, estimate finish Mon May 12 00:01:44 2008
  4.83% done, estimate finish Mon May 12 00:01:40 2008
  4.85% done, estimate finish Mon May 12 00:01:35 2008
  4.88% done, estimate finish Mon May 12 00:01:30 2008
  4.90% done, estimate finish Mon May 12 00:01:25 2008
  4.93% done, estimate finish Mon May 12 00:01:21 2008
  4.95% done, estimate finish Mon May 12 00:01:37 2008
  4.98% done, estimate finish Mon May 12 00:01:32 2008
  5.01% done, estimate finish Mon May 12 00:01:27 2008
  5.03% done, estimate finish Mon May 12 00:01:23 2008
  5.06% done, estimate finish Mon May 12 00:01:18 2008
  5.08% done, estimate finish Mon May 12 00:01:14 2008
  5.11% done, estimate finish Mon May 12 00:01:10 2008
  5.14% done, estimate finish Mon May 12 00:01:05 2008
  5.16% done, estimate finish Mon May 12 00:01:01 2008
  5.19% done, estimate finish Mon May 12 00:00:57 2008
  5.21% done, estimate finish Mon May 12 00:01:12 2008
  5.24% done, estimate finish Mon May 12 00:01:07 2008
  5.26% done, estimate finish Mon May 12 00:01:03 2008
  5.29% done, estimate finish Mon May 12 00:00:59 2008
  5.32% done, estimate finish Mon May 12 00:00:55 2008
  5.34% done, estimate finish Mon May 12 00:00:51 2008
  5.37% done, estimate finish Mon May 12 00:00:47 2008
  5.39% done, estimate finish Mon May 12 00:00:43 2008
  5.42% done, estimate finish Mon May 12 00:00:39 2008
  5.45% done, estimate finish Mon May 12 00:00:35 2008
  5.47% done, estimate finish Mon May 12 00:00:31 2008
  5.50% done, estimate finish Mon May 12 00:00:45 2008
  5.52% done, estimate finish Mon May 12 00:00:41 2008
  5.55% done, estimate finish Mon May 12 00:00:38 2008
  5.57% done, estimate finish Mon May 12 00:00:34 2008
  5.60% done, estimate finish Mon May 12 00:00:30 2008
  5.63% done, estimate finish Mon May 12 00:00:26 2008
  5.65% done, estimate finish Mon May 12 00:00:22 2008
  5.68% done, estimate finish Mon May 12 00:00:19 2008
  5.70% done, estimate finish Mon May 12 00:00:15 2008
  5.73% done, estimate finish Mon May 12 00:00:11 2008
  5.75% done, estimate finish Mon May 12 00:00:25 2008
  5.78% done, estimate finish Mon May 12 00:00:22 2008
  5.81% done, estimate finish Mon May 12 00:00:18 2008
  5.83% done, estimate finish Mon May 12 00:00:14 2008
  5.86% done, estimate finish Mon May 12 00:00:11 2008
  5.88% done, estimate finish Mon May 12 00:00:07 2008
  5.91% done, estimate finish Mon May 12 00:00:04 2008
  5.94% done, estimate finish Mon May 12 00:00:00 2008
  5.96% done, estimate finish Sun May 11 23:59:57 2008
  5.99% done, estimate finish Sun May 11 23:59:54 2008
  6.01% done, estimate finish Sun May 11 23:59:50 2008
  6.04% done, estimate finish Mon May 12 00:00:03 2008
  6.06% done, estimate finish Mon May 12 00:00:00 2008
  6.09% done, estimate finish Sun May 11 23:59:57 2008
  6.12% done, estimate finish Sun May 11 23:59:53 2008
  6.14% done, estimate finish Sun May 11 23:59:50 2008
  6.17% done, estimate finish Sun May 11 23:59:47 2008
  6.19% done, estimate finish Sun May 11 23:59:44 2008
  6.22% done, estimate finish Sun May 11 23:59:40 2008
  6.25% done, estimate finish Sun May 11 23:59:37 2008
  6.27% done, estimate finish Sun May 11 23:59:34 2008
  6.30% done, estimate finish Sun May 11 23:59:47 2008
  6.32% done, estimate finish Sun May 11 23:59:44 2008
  6.35% done, estimate finish Sun May 11 23:59:40 2008
  6.37% done, estimate finish Sun May 11 23:59:37 2008
  6.40% done, estimate finish Sun May 11 23:59:34 2008
  6.43% done, estimate finish Sun May 11 23:59:31 2008
  6.45% done, estimate finish Sun May 11 23:59:28 2008
  6.48% done, estimate finish Sun May 11 23:59:25 2008
  6.50% done, estimate finish Sun May 11 23:59:22 2008
  6.53% done, estimate finish Sun May 11 23:59:19 2008
  6.56% done, estimate finish Sun May 11 23:59:16 2008
  6.58% done, estimate finish Sun May 11 23:59:28 2008
  6.61% done, estimate finish Sun May 11 23:59:25 2008
  6.63% done, estimate finish Sun May 11 23:59:22 2008
  6.66% done, estimate finish Sun May 11 23:59:19 2008
  6.68% done, estimate finish Sun May 11 23:59:17 2008
  6.71% done, estimate finish Sun May 11 23:59:14 2008
  6.74% done, estimate finish Sun May 11 23:59:11 2008
  6.76% done, estimate finish Sun May 11 23:59:08 2008
  6.79% done, estimate finish Sun May 11 23:59:05 2008
  6.81% done, estimate finish Sun May 11 23:59:02 2008
  6.84% done, estimate finish Sun May 11 23:59:00 2008
  6.86% done, estimate finish Sun May 11 23:59:11 2008
  6.89% done, estimate finish Sun May 11 23:59:09 2008
  6.92% done, estimate finish Sun May 11 23:59:06 2008
  6.94% done, estimate finish Sun May 11 23:59:03 2008
  6.97% done, estimate finish Sun May 11 23:59:00 2008
  6.99% done, estimate finish Sun May 11 23:58:58 2008
  7.02% done, estimate finish Sun May 11 23:58:55 2008
  7.04% done, estimate finish Sun May 11 23:58:52 2008
  7.07% done, estimate finish Sun May 11 23:58:50 2008
  7.10% done, estimate finish Sun May 11 23:58:47 2008
  7.12% done, estimate finish Sun May 11 23:58:59 2008
  7.15% done, estimate finish Sun May 11 23:58:56 2008
  7.17% done, estimate finish Sun May 11 23:58:53 2008
  7.20% done, estimate finish Sun May 11 23:58:51 2008
  7.23% done, estimate finish Sun May 11 23:58:48 2008
  7.25% done, estimate finish Sun May 11 23:58:46 2008
  7.28% done, estimate finish Sun May 11 23:58:43 2008
  7.30% done, estimate finish Sun May 11 23:58:41 2008
  7.33% done, estimate finish Sun May 11 23:58:38 2008
  7.35% done, estimate finish Sun May 11 23:58:36 2008
  7.38% done, estimate finish Sun May 11 23:58:33 2008
  7.41% done, estimate finish Sun May 11 23:58:44 2008
  7.43% done, estimate finish Sun May 11 23:58:42 2008
  7.46% done, estimate finish Sun May 11 23:58:39 2008
  7.48% done, estimate finish Sun May 11 23:58:37 2008
  7.51% done, estimate finish Sun May 11 23:58:34 2008
  7.54% done, estimate finish Sun May 11 23:58:32 2008
  7.56% done, estimate finish Sun May 11 23:58:29 2008
  7.59% done, estimate finish Sun May 11 23:58:27 2008
  7.61% done, estimate finish Sun May 11 23:58:25 2008
  7.64% done, estimate finish Sun May 11 23:58:22 2008
  7.66% done, estimate finish Sun May 11 23:58:20 2008
  7.69% done, estimate finish Sun May 11 23:58:31 2008
  7.72% done, estimate finish Sun May 11 23:58:28 2008
  7.74% done, estimate finish Sun May 11 23:58:26 2008
  7.77% done, estimate finish Sun May 11 23:58:24 2008
  7.79% done, estimate finish Sun May 11 23:58:21 2008
  7.82% done, estimate finish Sun May 11 23:58:19 2008
  7.84% done, estimate finish Sun May 11 23:58:17 2008
  7.87% done, estimate finish Sun May 11 23:58:27 2008
  7.90% done, estimate finish Sun May 11 23:58:25 2008
  7.92% done, estimate finish Sun May 11 23:58:23 2008
  7.95% done, estimate finish Sun May 11 23:58:20 2008
  7.97% done, estimate finish Sun May 11 23:58:18 2008
  8.00% done, estimate finish Sun May 11 23:58:16 2008
  8.03% done, estimate finish Sun May 11 23:58:14 2008
  8.05% done, estimate finish Sun May 11 23:58:12 2008
  8.08% done, estimate finish Sun May 11 23:58:09 2008
  8.10% done, estimate finish Sun May 11 23:58:07 2008
  8.13% done, estimate finish Sun May 11 23:58:05 2008
  8.15% done, estimate finish Sun May 11 23:58:15 2008
  8.18% done, estimate finish Sun May 11 23:58:13 2008
  8.21% done, estimate finish Sun May 11 23:58:11 2008
  8.23% done, estimate finish Sun May 11 23:58:09 2008
  8.26% done, estimate finish Sun May 11 23:58:07 2008
  8.28% done, estimate finish Sun May 11 23:58:05 2008
  8.31% done, estimate finish Sun May 11 23:58:02 2008
  8.34% done, estimate finish Sun May 11 23:58:00 2008
  8.36% done, estimate finish Sun May 11 23:57:58 2008
  8.39% done, estimate finish Sun May 11 23:57:56 2008
  8.41% done, estimate finish Sun May 11 23:57:54 2008
  8.44% done, estimate finish Sun May 11 23:58:04 2008
  8.46% done, estimate finish Sun May 11 23:58:02 2008
  8.49% done, estimate finish Sun May 11 23:58:00 2008
  8.52% done, estimate finish Sun May 11 23:57:58 2008
  8.54% done, estimate finish Sun May 11 23:57:56 2008
  8.57% done, estimate finish Sun May 11 23:57:54 2008
  8.59% done, estimate finish Sun May 11 23:57:52 2008
  8.62% done, estimate finish Sun May 11 23:57:50 2008
  8.65% done, estimate finish Sun May 11 23:57:48 2008
  8.67% done, estimate finish Sun May 11 23:57:46 2008
  8.70% done, estimate finish Sun May 11 23:57:44 2008
  8.72% done, estimate finish Sun May 11 23:57:53 2008
  8.75% done, estimate finish Sun May 11 23:57:51 2008
  8.77% done, estimate finish Sun May 11 23:57:50 2008
  8.80% done, estimate finish Sun May 11 23:57:48 2008
  8.83% done, estimate finish Sun May 11 23:57:46 2008
  8.85% done, estimate finish Sun May 11 23:57:44 2008
  8.88% done, estimate finish Sun May 11 23:57:42 2008
  8.90% done, estimate finish Sun May 11 23:57:40 2008
  8.93% done, estimate finish Sun May 11 23:57:38 2008
  8.95% done, estimate finish Sun May 11 23:57:36 2008
  8.98% done, estimate finish Sun May 11 23:57:34 2008
  9.01% done, estimate finish Sun May 11 23:57:44 2008
  9.03% done, estimate finish Sun May 11 23:57:42 2008
  9.06% done, estimate finish Sun May 11 23:57:40 2008
  9.08% done, estimate finish Sun May 11 23:57:38 2008
  9.11% done, estimate finish Sun May 11 23:57:36 2008
  9.14% done, estimate finish Sun May 11 23:57:34 2008
  9.16% done, estimate finish Sun May 11 23:57:33 2008
  9.19% done, estimate finish Sun May 11 23:57:31 2008
  9.21% done, estimate finish Sun May 11 23:57:29 2008
  9.24% done, estimate finish Sun May 11 23:57:27 2008
  9.26% done, estimate finish Sun May 11 23:57:25 2008
  9.29% done, estimate finish Sun May 11 23:57:34 2008
  9.32% done, estimate finish Sun May 11 23:57:33 2008
  9.34% done, estimate finish Sun May 11 23:57:31 2008
  9.37% done, estimate finish Sun May 11 23:57:29 2008
  9.39% done, estimate finish Sun May 11 23:57:27 2008
  9.42% done, estimate finish Sun May 11 23:57:26 2008
  9.45% done, estimate finish Sun May 11 23:57:24 2008
  9.47% done, estimate finish Sun May 11 23:57:22 2008
  9.50% done, estimate finish Sun May 11 23:57:20 2008
  9.52% done, estimate finish Sun May 11 23:57:19 2008
  9.55% done, estimate finish Sun May 11 23:57:17 2008
  9.57% done, estimate finish Sun May 11 23:57:26 2008
  9.60% done, estimate finish Sun May 11 23:57:24 2008
  9.63% done, estimate finish Sun May 11 23:57:22 2008
  9.65% done, estimate finish Sun May 11 23:57:21 2008
  9.68% done, estimate finish Sun May 11 23:57:19 2008
  9.70% done, estimate finish Sun May 11 23:57:17 2008
  9.73% done, estimate finish Sun May 11 23:57:16 2008
  9.75% done, estimate finish Sun May 11 23:57:14 2008
  9.78% done, estimate finish Sun May 11 23:57:12 2008
  9.81% done, estimate finish Sun May 11 23:57:11 2008
  9.83% done, estimate finish Sun May 11 23:57:09 2008
  9.86% done, estimate finish Sun May 11 23:57:17 2008
  9.88% done, estimate finish Sun May 11 23:57:16 2008
  9.91% done, estimate finish Sun May 11 23:57:14 2008
  9.93% done, estimate finish Sun May 11 23:57:13 2008
  9.96% done, estimate finish Sun May 11 23:57:11 2008
  9.99% done, estimate finish Sun May 11 23:57:09 2008
 10.01% done, estimate finish Sun May 11 23:57:08 2008
 10.04% done, estimate finish Sun May 11 23:57:06 2008
 10.06% done, estimate finish Sun May 11 23:57:05 2008
 10.09% done, estimate finish Sun May 11 23:57:03 2008
 10.12% done, estimate finish Sun May 11 23:57:01 2008
 10.14% done, estimate finish Sun May 11 23:57:10 2008
 10.17% done, estimate finish Sun May 11 23:57:08 2008
 10.19% done, estimate finish Sun May 11 23:57:07 2008
 10.22% done, estimate finish Sun May 11 23:57:05 2008
 10.24% done, estimate finish Sun May 11 23:57:03 2008
 10.27% done, estimate finish Sun May 11 23:57:02 2008
 10.30% done, estimate finish Sun May 11 23:57:00 2008
 10.32% done, estimate finish Sun May 11 23:56:59 2008
 10.35% done, estimate finish Sun May 11 23:56:57 2008
 10.37% done, estimate finish Sun May 11 23:56:56 2008
 10.40% done, estimate finish Sun May 11 23:56:54 2008
 10.43% done, estimate finish Sun May 11 23:56:53 2008
 10.45% done, estimate finish Sun May 11 23:57:01 2008
 10.48% done, estimate finish Sun May 11 23:56:59 2008
 10.50% done, estimate finish Sun May 11 23:56:58 2008
 10.53% done, estimate finish Sun May 11 23:56:56 2008
 10.55% done, estimate finish Sun May 11 23:56:55 2008
 10.58% done, estimate finish Sun May 11 23:56:53 2008
 10.61% done, estimate finish Sun May 11 23:56:52 2008
 10.63% done, estimate finish Sun May 11 23:56:50 2008
 10.66% done, estimate finish Sun May 11 23:56:49 2008
 10.68% done, estimate finish Sun May 11 23:56:48 2008
 10.71% done, estimate finish Sun May 11 23:56:46 2008
 10.74% done, estimate finish Sun May 11 23:56:54 2008
 10.76% done, estimate finish Sun May 11 23:56:53 2008
 10.79% done, estimate finish Sun May 11 23:56:51 2008
 10.81% done, estimate finish Sun May 11 23:56:50 2008
 10.84% done, estimate finish Sun May 11 23:56:48 2008
 10.86% done, estimate finish Sun May 11 23:56:47 2008
 10.89% done, estimate finish Sun May 11 23:56:45 2008
 10.92% done, estimate finish Sun May 11 23:56:44 2008
 10.94% done, estimate finish Sun May 11 23:56:43 2008
 10.97% done, estimate finish Sun May 11 23:56:41 2008
 10.99% done, estimate finish Sun May 11 23:56:40 2008
 11.02% done, estimate finish Sun May 11 23:56:47 2008
 11.04% done, estimate finish Sun May 11 23:56:46 2008
 11.07% done, estimate finish Sun May 11 23:56:45 2008
 11.10% done, estimate finish Sun May 11 23:56:43 2008
 11.12% done, estimate finish Sun May 11 23:56:42 2008
 11.15% done, estimate finish Sun May 11 23:56:41 2008
 11.17% done, estimate finish Sun May 11 23:56:39 2008
 11.20% done, estimate finish Sun May 11 23:56:38 2008
 11.23% done, estimate finish Sun May 11 23:56:36 2008
 11.25% done, estimate finish Sun May 11 23:56:35 2008
 11.28% done, estimate finish Sun May 11 23:56:34 2008
 11.30% done, estimate finish Sun May 11 23:56:32 2008
 11.33% done, estimate finish Sun May 11 23:56:40 2008
 11.35% done, estimate finish Sun May 11 23:56:39 2008
 11.38% done, estimate finish Sun May 11 23:56:37 2008
 11.41% done, estimate finish Sun May 11 23:56:36 2008
 11.43% done, estimate finish Sun May 11 23:56:35 2008
 11.46% done, estimate finish Sun May 11 23:56:33 2008
 11.48% done, estimate finish Sun May 11 23:56:32 2008
 11.51% done, estimate finish Sun May 11 23:56:31 2008
 11.54% done, estimate finish Sun May 11 23:56:29 2008
 11.56% done, estimate finish Sun May 11 23:56:28 2008
 11.59% done, estimate finish Sun May 11 23:56:27 2008
 11.61% done, estimate finish Sun May 11 23:56:34 2008
 11.64% done, estimate finish Sun May 11 23:56:33 2008
 11.66% done, estimate finish Sun May 11 23:56:31 2008
 11.69% done, estimate finish Sun May 11 23:56:30 2008
 11.72% done, estimate finish Sun May 11 23:56:29 2008
 11.74% done, estimate finish Sun May 11 23:56:28 2008
 11.77% done, estimate finish Sun May 11 23:56:26 2008
 11.79% done, estimate finish Sun May 11 23:56:25 2008
 11.82% done, estimate finish Sun May 11 23:56:24 2008
 11.84% done, estimate finish Sun May 11 23:56:23 2008
 11.87% done, estimate finish Sun May 11 23:56:21 2008
 11.90% done, estimate finish Sun May 11 23:56:20 2008
 11.92% done, estimate finish Sun May 11 23:56:27 2008
 11.95% done, estimate finish Sun May 11 23:56:26 2008
 11.97% done, estimate finish Sun May 11 23:56:25 2008
 12.00% done, estimate finish Sun May 11 23:56:24 2008
 12.03% done, estimate finish Sun May 11 23:56:22 2008
 12.05% done, estimate finish Sun May 11 23:56:21 2008
 12.08% done, estimate finish Sun May 11 23:56:20 2008
 12.10% done, estimate finish Sun May 11 23:56:19 2008
 12.13% done, estimate finish Sun May 11 23:56:17 2008
 12.15% done, estimate finish Sun May 11 23:56:16 2008
 12.18% done, estimate finish Sun May 11 23:56:15 2008
 12.21% done, estimate finish Sun May 11 23:56:22 2008
 12.23% done, estimate finish Sun May 11 23:56:21 2008
 12.26% done, estimate finish Sun May 11 23:56:20 2008
 12.28% done, estimate finish Sun May 11 23:56:18 2008
 12.31% done, estimate finish Sun May 11 23:56:17 2008
 12.34% done, estimate finish Sun May 11 23:56:16 2008
 12.36% done, estimate finish Sun May 11 23:56:15 2008
 12.39% done, estimate finish Sun May 11 23:56:14 2008
 12.41% done, estimate finish Sun May 11 23:56:12 2008
 12.44% done, estimate finish Sun May 11 23:56:11 2008
 12.46% done, estimate finish Sun May 11 23:56:10 2008
 12.49% done, estimate finish Sun May 11 23:56:09 2008
 12.52% done, estimate finish Sun May 11 23:56:16 2008
 12.54% done, estimate finish Sun May 11 23:56:15 2008
 12.57% done, estimate finish Sun May 11 23:56:13 2008
 12.59% done, estimate finish Sun May 11 23:56:12 2008
 12.62% done, estimate finish Sun May 11 23:56:11 2008
 12.65% done, estimate finish Sun May 11 23:56:10 2008
 12.67% done, estimate finish Sun May 11 23:56:09 2008
 12.70% done, estimate finish Sun May 11 23:56:08 2008
 12.72% done, estimate finish Sun May 11 23:56:07 2008
 12.75% done, estimate finish Sun May 11 23:56:05 2008
 12.77% done, estimate finish Sun May 11 23:56:04 2008
 12.80% done, estimate finish Sun May 11 23:56:11 2008
 12.83% done, estimate finish Sun May 11 23:56:10 2008
 12.85% done, estimate finish Sun May 11 23:56:09 2008
 12.88% done, estimate finish Sun May 11 23:56:08 2008
 12.90% done, estimate finish Sun May 11 23:56:07 2008
 12.93% done, estimate finish Sun May 11 23:56:05 2008
 12.95% done, estimate finish Sun May 11 23:56:04 2008
 12.98% done, estimate finish Sun May 11 23:56:03 2008
 13.01% done, estimate finish Sun May 11 23:56:02 2008
 13.03% done, estimate finish Sun May 11 23:56:01 2008
 13.06% done, estimate finish Sun May 11 23:56:00 2008
 13.08% done, estimate finish Sun May 11 23:55:59 2008
 13.11% done, estimate finish Sun May 11 23:56:05 2008
 13.14% done, estimate finish Sun May 11 23:56:04 2008
 13.16% done, estimate finish Sun May 11 23:56:03 2008
 13.19% done, estimate finish Sun May 11 23:56:02 2008
 13.21% done, estimate finish Sun May 11 23:56:01 2008
 13.24% done, estimate finish Sun May 11 23:56:00 2008
 13.26% done, estimate finish Sun May 11 23:55:59 2008
 13.29% done, estimate finish Sun May 11 23:55:58 2008
 13.32% done, estimate finish Sun May 11 23:55:57 2008
 13.34% done, estimate finish Sun May 11 23:55:56 2008
 13.37% done, estimate finish Sun May 11 23:55:55 2008
 13.39% done, estimate finish Sun May 11 23:55:54 2008
 13.42% done, estimate finish Sun May 11 23:56:00 2008
 13.45% done, estimate finish Sun May 11 23:55:59 2008
 13.47% done, estimate finish Sun May 11 23:55:58 2008
 13.50% done, estimate finish Sun May 11 23:55:57 2008
 13.52% done, estimate finish Sun May 11 23:55:56 2008
 13.55% done, estimate finish Sun May 11 23:55:55 2008
 13.57% done, estimate finish Sun May 11 23:55:54 2008
 13.60% done, estimate finish Sun May 11 23:55:53 2008
 13.63% done, estimate finish Sun May 11 23:55:52 2008
 13.65% done, estimate finish Sun May 11 23:55:51 2008
 13.68% done, estimate finish Sun May 11 23:55:50 2008
 13.70% done, estimate finish Sun May 11 23:55:49 2008
 13.73% done, estimate finish Sun May 11 23:55:55 2008
 13.75% done, estimate finish Sun May 11 23:55:54 2008
 13.78% done, estimate finish Sun May 11 23:55:53 2008
 13.81% done, estimate finish Sun May 11 23:55:52 2008
 13.83% done, estimate finish Sun May 11 23:55:51 2008
 13.86% done, estimate finish Sun May 11 23:55:50 2008
 13.88% done, estimate finish Sun May 11 23:55:49 2008
 13.91% done, estimate finish Sun May 11 23:55:48 2008
 13.94% done, estimate finish Sun May 11 23:55:47 2008
 13.96% done, estimate finish Sun May 11 23:55:46 2008
 13.99% done, estimate finish Sun May 11 23:55:45 2008
 14.01% done, estimate finish Sun May 11 23:55:44 2008
 14.04% done, estimate finish Sun May 11 23:55:50 2008
 14.06% done, estimate finish Sun May 11 23:55:49 2008
 14.09% done, estimate finish Sun May 11 23:55:48 2008
 14.12% done, estimate finish Sun May 11 23:55:47 2008
 14.14% done, estimate finish Sun May 11 23:55:46 2008
 14.17% done, estimate finish Sun May 11 23:55:45 2008
 14.19% done, estimate finish Sun May 11 23:55:44 2008
 14.22% done, estimate finish Sun May 11 23:55:43 2008
 14.24% done, estimate finish Sun May 11 23:55:42 2008
 14.27% done, estimate finish Sun May 11 23:55:41 2008
 14.30% done, estimate finish Sun May 11 23:55:40 2008
 14.32% done, estimate finish Sun May 11 23:55:39 2008
 14.35% done, estimate finish Sun May 11 23:55:45 2008
 14.37% done, estimate finish Sun May 11 23:55:44 2008
 14.40% done, estimate finish Sun May 11 23:55:43 2008
 14.43% done, estimate finish Sun May 11 23:55:42 2008
 14.45% done, estimate finish Sun May 11 23:55:41 2008
 14.48% done, estimate finish Sun May 11 23:55:40 2008
 14.50% done, estimate finish Sun May 11 23:55:39 2008
 14.53% done, estimate finish Sun May 11 23:55:39 2008
 14.55% done, estimate finish Sun May 11 23:55:38 2008
 14.58% done, estimate finish Sun May 11 23:55:37 2008
 14.61% done, estimate finish Sun May 11 23:55:36 2008
 14.63% done, estimate finish Sun May 11 23:55:42 2008
 14.66% done, estimate finish Sun May 11 23:55:41 2008
 14.68% done, estimate finish Sun May 11 23:55:40 2008
 14.71% done, estimate finish Sun May 11 23:55:39 2008
 14.73% done, estimate finish Sun May 11 23:55:38 2008
 14.76% done, estimate finish Sun May 11 23:55:37 2008
 14.79% done, estimate finish Sun May 11 23:55:36 2008
 14.81% done, estimate finish Sun May 11 23:55:35 2008
 14.84% done, estimate finish Sun May 11 23:55:34 2008
 14.86% done, estimate finish Sun May 11 23:55:33 2008
 14.89% done, estimate finish Sun May 11 23:55:32 2008
 14.92% done, estimate finish Sun May 11 23:55:31 2008
 14.94% done, estimate finish Sun May 11 23:55:31 2008
 14.97% done, estimate finish Sun May 11 23:55:36 2008
 14.99% done, estimate finish Sun May 11 23:55:35 2008
 15.02% done, estimate finish Sun May 11 23:55:35 2008
 15.04% done, estimate finish Sun May 11 23:55:34 2008
 15.07% done, estimate finish Sun May 11 23:55:33 2008
 15.10% done, estimate finish Sun May 11 23:55:32 2008
 15.12% done, estimate finish Sun May 11 23:55:31 2008
 15.15% done, estimate finish Sun May 11 23:55:30 2008
 15.17% done, estimate finish Sun May 11 23:55:29 2008
 15.20% done, estimate finish Sun May 11 23:55:28 2008
 15.23% done, estimate finish Sun May 11 23:55:27 2008
 15.25% done, estimate finish Sun May 11 23:55:27 2008
 15.28% done, estimate finish Sun May 11 23:55:32 2008
 15.30% done, estimate finish Sun May 11 23:55:31 2008
 15.33% done, estimate finish Sun May 11 23:55:30 2008
 15.35% done, estimate finish Sun May 11 23:55:30 2008
 15.38% done, estimate finish Sun May 11 23:55:29 2008
 15.41% done, estimate finish Sun May 11 23:55:28 2008
 15.43% done, estimate finish Sun May 11 23:55:27 2008
 15.46% done, estimate finish Sun May 11 23:55:26 2008
 15.48% done, estimate finish Sun May 11 23:55:25 2008
 15.51% done, estimate finish Sun May 11 23:55:24 2008
 15.53% done, estimate finish Sun May 11 23:55:23 2008
 15.56% done, estimate finish Sun May 11 23:55:23 2008
 15.59% done, estimate finish Sun May 11 23:55:28 2008
 15.61% done, estimate finish Sun May 11 23:55:27 2008
 15.64% done, estimate finish Sun May 11 23:55:26 2008
 15.66% done, estimate finish Sun May 11 23:55:26 2008
 15.69% done, estimate finish Sun May 11 23:55:25 2008
 15.72% done, estimate finish Sun May 11 23:55:24 2008
 15.74% done, estimate finish Sun May 11 23:55:23 2008
 15.77% done, estimate finish Sun May 11 23:55:22 2008
 15.79% done, estimate finish Sun May 11 23:55:21 2008
 15.82% done, estimate finish Sun May 11 23:55:21 2008
 15.84% done, estimate finish Sun May 11 23:55:20 2008
 15.87% done, estimate finish Sun May 11 23:55:19 2008
 15.90% done, estimate finish Sun May 11 23:55:24 2008
 15.92% done, estimate finish Sun May 11 23:55:24 2008
 15.95% done, estimate finish Sun May 11 23:55:23 2008
 15.97% done, estimate finish Sun May 11 23:55:22 2008
 16.00% done, estimate finish Sun May 11 23:55:21 2008
 16.03% done, estimate finish Sun May 11 23:55:20 2008
 16.05% done, estimate finish Sun May 11 23:55:19 2008
 16.08% done, estimate finish Sun May 11 23:55:19 2008
 16.10% done, estimate finish Sun May 11 23:55:18 2008
 16.13% done, estimate finish Sun May 11 23:55:17 2008
 16.15% done, estimate finish Sun May 11 23:55:16 2008
 16.18% done, estimate finish Sun May 11 23:55:15 2008
 16.21% done, estimate finish Sun May 11 23:55:21 2008
 16.23% done, estimate finish Sun May 11 23:55:20 2008
 16.26% done, estimate finish Sun May 11 23:55:19 2008
 16.28% done, estimate finish Sun May 11 23:55:18 2008
 16.31% done, estimate finish Sun May 11 23:55:17 2008
 16.33% done, estimate finish Sun May 11 23:55:17 2008
 16.36% done, estimate finish Sun May 11 23:55:16 2008
 16.39% done, estimate finish Sun May 11 23:55:15 2008
 16.41% done, estimate finish Sun May 11 23:55:14 2008
 16.44% done, estimate finish Sun May 11 23:55:13 2008
 16.46% done, estimate finish Sun May 11 23:55:13 2008
 16.49% done, estimate finish Sun May 11 23:55:12 2008
 16.52% done, estimate finish Sun May 11 23:55:17 2008
 16.54% done, estimate finish Sun May 11 23:55:16 2008
 16.57% done, estimate finish Sun May 11 23:55:16 2008
 16.59% done, estimate finish Sun May 11 23:55:15 2008
 16.62% done, estimate finish Sun May 11 23:55:14 2008
 16.64% done, estimate finish Sun May 11 23:55:13 2008
 16.67% done, estimate finish Sun May 11 23:55:12 2008
 16.70% done, estimate finish Sun May 11 23:55:12 2008
 16.72% done, estimate finish Sun May 11 23:55:11 2008
 16.75% done, estimate finish Sun May 11 23:55:10 2008
 16.77% done, estimate finish Sun May 11 23:55:09 2008
 16.80% done, estimate finish Sun May 11 23:55:09 2008
 16.83% done, estimate finish Sun May 11 23:55:14 2008
 16.85% done, estimate finish Sun May 11 23:55:13 2008
 16.88% done, estimate finish Sun May 11 23:55:12 2008
 16.90% done, estimate finish Sun May 11 23:55:11 2008
 16.93% done, estimate finish Sun May 11 23:55:11 2008
 16.95% done, estimate finish Sun May 11 23:55:10 2008
 16.98% done, estimate finish Sun May 11 23:55:09 2008
 17.01% done, estimate finish Sun May 11 23:55:08 2008
 17.03% done, estimate finish Sun May 11 23:55:08 2008
 17.06% done, estimate finish Sun May 11 23:55:07 2008
 17.08% done, estimate finish Sun May 11 23:55:06 2008
 17.11% done, estimate finish Sun May 11 23:55:05 2008
 17.14% done, estimate finish Sun May 11 23:55:05 2008
 17.16% done, estimate finish Sun May 11 23:55:10 2008
 17.19% done, estimate finish Sun May 11 23:55:09 2008
 17.21% done, estimate finish Sun May 11 23:55:08 2008
 17.24% done, estimate finish Sun May 11 23:55:07 2008
 17.26% done, estimate finish Sun May 11 23:55:07 2008
 17.29% done, estimate finish Sun May 11 23:55:06 2008
 17.32% done, estimate finish Sun May 11 23:55:05 2008
 17.34% done, estimate finish Sun May 11 23:55:04 2008
 17.37% done, estimate finish Sun May 11 23:55:04 2008
 17.39% done, estimate finish Sun May 11 23:55:03 2008
 17.42% done, estimate finish Sun May 11 23:55:02 2008
 17.44% done, estimate finish Sun May 11 23:55:01 2008
 17.47% done, estimate finish Sun May 11 23:55:06 2008
 17.50% done, estimate finish Sun May 11 23:55:06 2008
 17.52% done, estimate finish Sun May 11 23:55:05 2008
 17.55% done, estimate finish Sun May 11 23:55:04 2008
 17.57% done, estimate finish Sun May 11 23:55:04 2008
 17.60% done, estimate finish Sun May 11 23:55:03 2008
 17.62% done, estimate finish Sun May 11 23:55:02 2008
 17.65% done, estimate finish Sun May 11 23:55:01 2008
 17.68% done, estimate finish Sun May 11 23:55:01 2008
 17.70% done, estimate finish Sun May 11 23:55:00 2008
 17.73% done, estimate finish Sun May 11 23:54:59 2008
 17.75% done, estimate finish Sun May 11 23:54:59 2008
 17.78% done, estimate finish Sun May 11 23:54:58 2008
 17.81% done, estimate finish Sun May 11 23:55:03 2008
 17.83% done, estimate finish Sun May 11 23:55:02 2008
 17.86% done, estimate finish Sun May 11 23:55:01 2008
 17.88% done, estimate finish Sun May 11 23:55:01 2008
 17.91% done, estimate finish Sun May 11 23:55:00 2008
 17.93% done, estimate finish Sun May 11 23:54:59 2008
 17.96% done, estimate finish Sun May 11 23:54:58 2008
 17.99% done, estimate finish Sun May 11 23:54:58 2008
 18.01% done, estimate finish Sun May 11 23:54:57 2008
 18.04% done, estimate finish Sun May 11 23:54:56 2008
 18.06% done, estimate finish Sun May 11 23:54:56 2008
 18.09% done, estimate finish Sun May 11 23:54:55 2008
 18.12% done, estimate finish Sun May 11 23:55:00 2008
 18.14% done, estimate finish Sun May 11 23:54:59 2008
 18.17% done, estimate finish Sun May 11 23:54:58 2008
 18.19% done, estimate finish Sun May 11 23:54:58 2008
 18.22% done, estimate finish Sun May 11 23:54:57 2008
 18.24% done, estimate finish Sun May 11 23:54:56 2008
 18.27% done, estimate finish Sun May 11 23:54:56 2008
 18.30% done, estimate finish Sun May 11 23:54:55 2008
 18.32% done, estimate finish Sun May 11 23:54:54 2008
 18.35% done, estimate finish Sun May 11 23:54:54 2008
 18.37% done, estimate finish Sun May 11 23:54:53 2008
 18.40% done, estimate finish Sun May 11 23:54:52 2008
 18.42% done, estimate finish Sun May 11 23:54:52 2008
 18.45% done, estimate finish Sun May 11 23:54:56 2008
 18.48% done, estimate finish Sun May 11 23:54:56 2008
 18.50% done, estimate finish Sun May 11 23:54:55 2008
 18.53% done, estimate finish Sun May 11 23:54:54 2008
 18.55% done, estimate finish Sun May 11 23:54:54 2008
 18.58% done, estimate finish Sun May 11 23:54:53 2008
 18.61% done, estimate finish Sun May 11 23:54:52 2008
 18.63% done, estimate finish Sun May 11 23:54:52 2008
 18.66% done, estimate finish Sun May 11 23:54:51 2008
 18.68% done, estimate finish Sun May 11 23:54:50 2008
 18.71% done, estimate finish Sun May 11 23:54:50 2008
 18.74% done, estimate finish Sun May 11 23:54:49 2008
 18.76% done, estimate finish Sun May 11 23:54:54 2008
 18.79% done, estimate finish Sun May 11 23:54:53 2008
 18.81% done, estimate finish Sun May 11 23:54:52 2008
 18.84% done, estimate finish Sun May 11 23:54:52 2008
 18.86% done, estimate finish Sun May 11 23:54:51 2008
 18.89% done, estimate finish Sun May 11 23:54:50 2008
 18.92% done, estimate finish Sun May 11 23:54:50 2008
 18.94% done, estimate finish Sun May 11 23:54:49 2008
 18.97% done, estimate finish Sun May 11 23:54:48 2008
 18.99% done, estimate finish Sun May 11 23:54:48 2008
 19.02% done, estimate finish Sun May 11 23:54:47 2008
 19.04% done, estimate finish Sun May 11 23:54:46 2008
 19.07% done, estimate finish Sun May 11 23:54:46 2008
 19.10% done, estimate finish Sun May 11 23:54:50 2008
 19.12% done, estimate finish Sun May 11 23:54:50 2008
 19.15% done, estimate finish Sun May 11 23:54:49 2008
 19.17% done, estimate finish Sun May 11 23:54:48 2008
 19.20% done, estimate finish Sun May 11 23:54:48 2008
 19.22% done, estimate finish Sun May 11 23:54:47 2008
 19.25% done, estimate finish Sun May 11 23:54:46 2008
 19.28% done, estimate finish Sun May 11 23:54:46 2008
 19.30% done, estimate finish Sun May 11 23:54:45 2008
 19.33% done, estimate finish Sun May 11 23:54:44 2008
 19.35% done, estimate finish Sun May 11 23:54:44 2008
 19.38% done, estimate finish Sun May 11 23:54:43 2008
 19.41% done, estimate finish Sun May 11 23:54:43 2008
 19.43% done, estimate finish Sun May 11 23:54:47 2008
 19.46% done, estimate finish Sun May 11 23:54:46 2008
 19.48% done, estimate finish Sun May 11 23:54:46 2008
 19.51% done, estimate finish Sun May 11 23:54:45 2008
 19.53% done, estimate finish Sun May 11 23:54:45 2008
 19.56% done, estimate finish Sun May 11 23:54:44 2008
 19.59% done, estimate finish Sun May 11 23:54:43 2008
 19.61% done, estimate finish Sun May 11 23:54:43 2008
 19.64% done, estimate finish Sun May 11 23:54:42 2008
 19.66% done, estimate finish Sun May 11 23:54:41 2008
 19.69% done, estimate finish Sun May 11 23:54:41 2008
 19.72% done, estimate finish Sun May 11 23:54:40 2008
 19.74% done, estimate finish Sun May 11 23:54:45 2008
 19.77% done, estimate finish Sun May 11 23:54:44 2008
 19.79% done, estimate finish Sun May 11 23:54:43 2008
 19.82% done, estimate finish Sun May 11 23:54:43 2008
 19.84% done, estimate finish Sun May 11 23:54:42 2008
 19.87% done, estimate finish Sun May 11 23:54:42 2008
 19.90% done, estimate finish Sun May 11 23:54:41 2008
 19.92% done, estimate finish Sun May 11 23:54:40 2008
 19.95% done, estimate finish Sun May 11 23:54:40 2008
 19.97% done, estimate finish Sun May 11 23:54:39 2008
 20.00% done, estimate finish Sun May 11 23:54:39 2008
 20.03% done, estimate finish Sun May 11 23:54:38 2008
 20.05% done, estimate finish Sun May 11 23:54:37 2008
 20.08% done, estimate finish Sun May 11 23:54:42 2008
 20.10% done, estimate finish Sun May 11 23:54:41 2008
 20.13% done, estimate finish Sun May 11 23:54:40 2008
 20.15% done, estimate finish Sun May 11 23:54:40 2008
 20.18% done, estimate finish Sun May 11 23:54:39 2008
 20.21% done, estimate finish Sun May 11 23:54:39 2008
 20.23% done, estimate finish Sun May 11 23:54:38 2008
 20.26% done, estimate finish Sun May 11 23:54:37 2008
 20.28% done, estimate finish Sun May 11 23:54:37 2008
 20.31% done, estimate finish Sun May 11 23:54:36 2008
 20.33% done, estimate finish Sun May 11 23:54:36 2008
 20.36% done, estimate finish Sun May 11 23:54:35 2008
 20.39% done, estimate finish Sun May 11 23:54:35 2008
 20.41% done, estimate finish Sun May 11 23:54:39 2008
 20.44% done, estimate finish Sun May 11 23:54:38 2008
 20.46% done, estimate finish Sun May 11 23:54:38 2008
 20.49% done, estimate finish Sun May 11 23:54:37 2008
 20.52% done, estimate finish Sun May 11 23:54:36 2008
 20.54% done, estimate finish Sun May 11 23:54:36 2008
 20.57% done, estimate finish Sun May 11 23:54:35 2008
 20.59% done, estimate finish Sun May 11 23:54:35 2008
 20.62% done, estimate finish Sun May 11 23:54:34 2008
 20.64% done, estimate finish Sun May 11 23:54:34 2008
 20.67% done, estimate finish Sun May 11 23:54:33 2008
 20.70% done, estimate finish Sun May 11 23:54:32 2008
 20.72% done, estimate finish Sun May 11 23:54:32 2008
 20.75% done, estimate finish Sun May 11 23:54:36 2008
 20.77% done, estimate finish Sun May 11 23:54:35 2008
 20.80% done, estimate finish Sun May 11 23:54:35 2008
 20.82% done, estimate finish Sun May 11 23:54:34 2008
 20.85% done, estimate finish Sun May 11 23:54:34 2008
 20.88% done, estimate finish Sun May 11 23:54:33 2008
 20.90% done, estimate finish Sun May 11 23:54:33 2008
 20.93% done, estimate finish Sun May 11 23:54:32 2008
 20.95% done, estimate finish Sun May 11 23:54:31 2008
 20.98% done, estimate finish Sun May 11 23:54:31 2008
 21.01% done, estimate finish Sun May 11 23:54:30 2008
 21.03% done, estimate finish Sun May 11 23:54:30 2008
 21.06% done, estimate finish Sun May 11 23:54:29 2008
 21.08% done, estimate finish Sun May 11 23:54:33 2008
 21.11% done, estimate finish Sun May 11 23:54:33 2008
 21.13% done, estimate finish Sun May 11 23:54:32 2008
 21.16% done, estimate finish Sun May 11 23:54:32 2008
 21.19% done, estimate finish Sun May 11 23:54:31 2008
 21.21% done, estimate finish Sun May 11 23:54:31 2008
 21.24% done, estimate finish Sun May 11 23:54:30 2008
 21.26% done, estimate finish Sun May 11 23:54:29 2008
 21.29% done, estimate finish Sun May 11 23:54:29 2008
 21.32% done, estimate finish Sun May 11 23:54:28 2008
 21.34% done, estimate finish Sun May 11 23:54:28 2008
 21.37% done, estimate finish Sun May 11 23:54:27 2008
 21.39% done, estimate finish Sun May 11 23:54:27 2008
 21.42% done, estimate finish Sun May 11 23:54:31 2008
 21.44% done, estimate finish Sun May 11 23:54:30 2008
 21.47% done, estimate finish Sun May 11 23:54:30 2008
 21.50% done, estimate finish Sun May 11 23:54:29 2008
 21.52% done, estimate finish Sun May 11 23:54:28 2008
 21.55% done, estimate finish Sun May 11 23:54:28 2008
 21.57% done, estimate finish Sun May 11 23:54:27 2008
 21.60% done, estimate finish Sun May 11 23:54:27 2008
 21.63% done, estimate finish Sun May 11 23:54:26 2008
 21.65% done, estimate finish Sun May 11 23:54:26 2008
 21.68% done, estimate finish Sun May 11 23:54:25 2008
 21.70% done, estimate finish Sun May 11 23:54:25 2008
 21.73% done, estimate finish Sun May 11 23:54:24 2008
 21.75% done, estimate finish Sun May 11 23:54:28 2008
 21.78% done, estimate finish Sun May 11 23:54:28 2008
 21.81% done, estimate finish Sun May 11 23:54:27 2008
 21.83% done, estimate finish Sun May 11 23:54:27 2008
 21.86% done, estimate finish Sun May 11 23:54:26 2008
 21.88% done, estimate finish Sun May 11 23:54:25 2008
 21.91% done, estimate finish Sun May 11 23:54:25 2008
 21.93% done, estimate finish Sun May 11 23:54:24 2008
 21.96% done, estimate finish Sun May 11 23:54:24 2008
 21.99% done, estimate finish Sun May 11 23:54:23 2008
 22.01% done, estimate finish Sun May 11 23:54:23 2008
 22.04% done, estimate finish Sun May 11 23:54:22 2008
 22.06% done, estimate finish Sun May 11 23:54:22 2008
 22.09% done, estimate finish Sun May 11 23:54:26 2008
 22.12% done, estimate finish Sun May 11 23:54:25 2008
 22.14% done, estimate finish Sun May 11 23:54:25 2008
 22.17% done, estimate finish Sun May 11 23:54:24 2008
 22.19% done, estimate finish Sun May 11 23:54:24 2008
 22.22% done, estimate finish Sun May 11 23:54:23 2008
 22.24% done, estimate finish Sun May 11 23:54:23 2008
 22.27% done, estimate finish Sun May 11 23:54:22 2008
 22.30% done, estimate finish Sun May 11 23:54:22 2008
 22.32% done, estimate finish Sun May 11 23:54:21 2008
 22.35% done, estimate finish Sun May 11 23:54:20 2008
 22.37% done, estimate finish Sun May 11 23:54:20 2008
 22.40% done, estimate finish Sun May 11 23:54:19 2008
 22.43% done, estimate finish Sun May 11 23:54:23 2008
 22.45% done, estimate finish Sun May 11 23:54:23 2008
 22.48% done, estimate finish Sun May 11 23:54:22 2008
 22.50% done, estimate finish Sun May 11 23:54:22 2008
 22.53% done, estimate finish Sun May 11 23:54:21 2008
 22.55% done, estimate finish Sun May 11 23:54:21 2008
 22.58% done, estimate finish Sun May 11 23:54:20 2008
 22.61% done, estimate finish Sun May 11 23:54:20 2008
 22.63% done, estimate finish Sun May 11 23:54:19 2008
 22.66% done, estimate finish Sun May 11 23:54:19 2008
 22.68% done, estimate finish Sun May 11 23:54:18 2008
 22.71% done, estimate finish Sun May 11 23:54:18 2008
 22.73% done, estimate finish Sun May 11 23:54:17 2008
 22.76% done, estimate finish Sun May 11 23:54:21 2008
 22.79% done, estimate finish Sun May 11 23:54:21 2008
 22.81% done, estimate finish Sun May 11 23:54:20 2008
 22.84% done, estimate finish Sun May 11 23:54:19 2008
 22.86% done, estimate finish Sun May 11 23:54:19 2008
 22.89% done, estimate finish Sun May 11 23:54:18 2008
 22.91% done, estimate finish Sun May 11 23:54:18 2008
 22.94% done, estimate finish Sun May 11 23:54:17 2008
 22.97% done, estimate finish Sun May 11 23:54:17 2008
 22.99% done, estimate finish Sun May 11 23:54:16 2008
 23.02% done, estimate finish Sun May 11 23:54:16 2008
 23.04% done, estimate finish Sun May 11 23:54:15 2008
 23.07% done, estimate finish Sun May 11 23:54:15 2008
 23.10% done, estimate finish Sun May 11 23:54:19 2008
 23.12% done, estimate finish Sun May 11 23:54:18 2008
 23.15% done, estimate finish Sun May 11 23:54:18 2008
 23.17% done, estimate finish Sun May 11 23:54:17 2008
 23.20% done, estimate finish Sun May 11 23:54:17 2008
 23.22% done, estimate finish Sun May 11 23:54:16 2008
 23.25% done, estimate finish Sun May 11 23:54:16 2008
 23.28% done, estimate finish Sun May 11 23:54:15 2008
 23.30% done, estimate finish Sun May 11 23:54:15 2008
 23.33% done, estimate finish Sun May 11 23:54:14 2008
 23.35% done, estimate finish Sun May 11 23:54:14 2008
 23.38% done, estimate finish Sun May 11 23:54:13 2008
 23.41% done, estimate finish Sun May 11 23:54:13 2008
 23.43% done, estimate finish Sun May 11 23:54:12 2008
 23.46% done, estimate finish Sun May 11 23:54:16 2008
 23.48% done, estimate finish Sun May 11 23:54:16 2008
 23.51% done, estimate finish Sun May 11 23:54:15 2008
 23.53% done, estimate finish Sun May 11 23:54:15 2008
 23.56% done, estimate finish Sun May 11 23:54:14 2008
 23.59% done, estimate finish Sun May 11 23:54:14 2008
 23.61% done, estimate finish Sun May 11 23:54:13 2008
 23.64% done, estimate finish Sun May 11 23:54:13 2008
 23.66% done, estimate finish Sun May 11 23:54:12 2008
 23.69% done, estimate finish Sun May 11 23:54:12 2008
 23.72% done, estimate finish Sun May 11 23:54:11 2008
 23.74% done, estimate finish Sun May 11 23:54:11 2008
 23.77% done, estimate finish Sun May 11 23:54:10 2008
 23.79% done, estimate finish Sun May 11 23:54:14 2008
 23.82% done, estimate finish Sun May 11 23:54:14 2008
 23.84% done, estimate finish Sun May 11 23:54:13 2008
 23.87% done, estimate finish Sun May 11 23:54:13 2008
 23.90% done, estimate finish Sun May 11 23:54:12 2008
 23.92% done, estimate finish Sun May 11 23:54:12 2008
 23.95% done, estimate finish Sun May 11 23:54:11 2008
 23.97% done, estimate finish Sun May 11 23:54:11 2008
 24.00% done, estimate finish Sun May 11 23:54:10 2008
 24.02% done, estimate finish Sun May 11 23:54:10 2008
 24.05% done, estimate finish Sun May 11 23:54:09 2008
 24.08% done, estimate finish Sun May 11 23:54:09 2008
 24.10% done, estimate finish Sun May 11 23:54:08 2008
 24.13% done, estimate finish Sun May 11 23:54:12 2008
 24.15% done, estimate finish Sun May 11 23:54:11 2008
 24.18% done, estimate finish Sun May 11 23:54:11 2008
 24.21% done, estimate finish Sun May 11 23:54:11 2008
 24.23% done, estimate finish Sun May 11 23:54:10 2008
 24.26% done, estimate finish Sun May 11 23:54:10 2008
 24.28% done, estimate finish Sun May 11 23:54:09 2008
 24.31% done, estimate finish Sun May 11 23:54:09 2008
 24.33% done, estimate finish Sun May 11 23:54:08 2008
 24.36% done, estimate finish Sun May 11 23:54:08 2008
 24.39% done, estimate finish Sun May 11 23:54:07 2008
 24.41% done, estimate finish Sun May 11 23:54:07 2008
 24.44% done, estimate finish Sun May 11 23:54:06 2008
 24.46% done, estimate finish Sun May 11 23:54:06 2008
 24.49% done, estimate finish Sun May 11 23:54:10 2008
 24.52% done, estimate finish Sun May 11 23:54:09 2008
 24.54% done, estimate finish Sun May 11 23:54:09 2008
 24.57% done, estimate finish Sun May 11 23:54:08 2008
 24.59% done, estimate finish Sun May 11 23:54:08 2008
 24.62% done, estimate finish Sun May 11 23:54:07 2008
 24.64% done, estimate finish Sun May 11 23:54:07 2008
 24.67% done, estimate finish Sun May 11 23:54:06 2008
 24.70% done, estimate finish Sun May 11 23:54:06 2008
 24.72% done, estimate finish Sun May 11 23:54:05 2008
 24.75% done, estimate finish Sun May 11 23:54:05 2008
 24.77% done, estimate finish Sun May 11 23:54:04 2008
 24.80% done, estimate finish Sun May 11 23:54:04 2008
 24.82% done, estimate finish Sun May 11 23:54:08 2008
 24.85% done, estimate finish Sun May 11 23:54:07 2008
 24.88% done, estimate finish Sun May 11 23:54:07 2008
 24.90% done, estimate finish Sun May 11 23:54:06 2008
 24.93% done, estimate finish Sun May 11 23:54:06 2008
 24.95% done, estimate finish Sun May 11 23:54:05 2008
 24.98% done, estimate finish Sun May 11 23:54:05 2008
 25.01% done, estimate finish Sun May 11 23:54:04 2008
 25.03% done, estimate finish Sun May 11 23:54:04 2008
 25.06% done, estimate finish Sun May 11 23:54:04 2008
 25.08% done, estimate finish Sun May 11 23:54:03 2008
 25.11% done, estimate finish Sun May 11 23:54:03 2008
 25.13% done, estimate finish Sun May 11 23:54:02 2008
 25.16% done, estimate finish Sun May 11 23:54:02 2008
 25.19% done, estimate finish Sun May 11 23:54:05 2008
 25.21% done, estimate finish Sun May 11 23:54:05 2008
 25.24% done, estimate finish Sun May 11 23:54:04 2008
 25.26% done, estimate finish Sun May 11 23:54:04 2008
 25.29% done, estimate finish Sun May 11 23:54:03 2008
 25.32% done, estimate finish Sun May 11 23:54:03 2008
 25.34% done, estimate finish Sun May 11 23:54:03 2008
 25.37% done, estimate finish Sun May 11 23:54:02 2008
 25.39% done, estimate finish Sun May 11 23:54:02 2008
 25.42% done, estimate finish Sun May 11 23:54:01 2008
 25.44% done, estimate finish Sun May 11 23:54:01 2008
 25.47% done, estimate finish Sun May 11 23:54:00 2008
 25.50% done, estimate finish Sun May 11 23:54:00 2008
 25.52% done, estimate finish Sun May 11 23:54:03 2008
 25.55% done, estimate finish Sun May 11 23:54:03 2008
 25.57% done, estimate finish Sun May 11 23:54:03 2008
 25.60% done, estimate finish Sun May 11 23:54:02 2008
 25.63% done, estimate finish Sun May 11 23:54:02 2008
 25.65% done, estimate finish Sun May 11 23:54:01 2008
 25.68% done, estimate finish Sun May 11 23:54:01 2008
 25.70% done, estimate finish Sun May 11 23:54:00 2008
 25.73% done, estimate finish Sun May 11 23:54:00 2008
 25.75% done, estimate finish Sun May 11 23:54:03 2008
 25.78% done, estimate finish Sun May 11 23:54:03 2008
 25.81% done, estimate finish Sun May 11 23:54:03 2008
 25.83% done, estimate finish Sun May 11 23:54:02 2008
 25.86% done, estimate finish Sun May 11 23:54:02 2008
 25.88% done, estimate finish Sun May 11 23:54:01 2008
 25.91% done, estimate finish Sun May 11 23:54:01 2008
 25.93% done, estimate finish Sun May 11 23:54:00 2008
 25.96% done, estimate finish Sun May 11 23:54:00 2008
 25.99% done, estimate finish Sun May 11 23:54:00 2008
 26.01% done, estimate finish Sun May 11 23:53:59 2008
 26.04% done, estimate finish Sun May 11 23:53:59 2008
 26.06% done, estimate finish Sun May 11 23:53:58 2008
 26.09% done, estimate finish Sun May 11 23:53:58 2008
 26.11% done, estimate finish Sun May 11 23:54:01 2008
 26.14% done, estimate finish Sun May 11 23:54:01 2008
 26.17% done, estimate finish Sun May 11 23:54:00 2008
 26.19% done, estimate finish Sun May 11 23:54:00 2008
 26.22% done, estimate finish Sun May 11 23:54:00 2008
 26.24% done, estimate finish Sun May 11 23:53:59 2008
 26.27% done, estimate finish Sun May 11 23:53:59 2008
 26.30% done, estimate finish Sun May 11 23:53:58 2008
 26.32% done, estimate finish Sun May 11 23:53:58 2008
 26.35% done, estimate finish Sun May 11 23:53:57 2008
 26.37% done, estimate finish Sun May 11 23:53:57 2008
 26.40% done, estimate finish Sun May 11 23:53:57 2008
 26.42% done, estimate finish Sun May 11 23:53:56 2008
 26.45% done, estimate finish Sun May 11 23:53:59 2008
 26.48% done, estimate finish Sun May 11 23:53:59 2008
 26.50% done, estimate finish Sun May 11 23:53:59 2008
 26.53% done, estimate finish Sun May 11 23:53:58 2008
 26.55% done, estimate finish Sun May 11 23:53:58 2008
 26.58% done, estimate finish Sun May 11 23:53:57 2008
 26.61% done, estimate finish Sun May 11 23:53:57 2008
 26.63% done, estimate finish Sun May 11 23:53:57 2008
 26.66% done, estimate finish Sun May 11 23:53:56 2008
 26.68% done, estimate finish Sun May 11 23:53:56 2008
 26.71% done, estimate finish Sun May 11 23:53:55 2008
 26.73% done, estimate finish Sun May 11 23:53:55 2008
 26.76% done, estimate finish Sun May 11 23:53:55 2008
 26.79% done, estimate finish Sun May 11 23:53:54 2008
 26.81% done, estimate finish Sun May 11 23:53:57 2008
 26.84% done, estimate finish Sun May 11 23:53:57 2008
 26.86% done, estimate finish Sun May 11 23:53:57 2008
 26.89% done, estimate finish Sun May 11 23:53:56 2008
 26.91% done, estimate finish Sun May 11 23:53:56 2008
 26.94% done, estimate finish Sun May 11 23:53:55 2008
 26.97% done, estimate finish Sun May 11 23:53:55 2008
 26.99% done, estimate finish Sun May 11 23:53:55 2008
 27.02% done, estimate finish Sun May 11 23:53:54 2008
 27.04% done, estimate finish Sun May 11 23:53:54 2008
 27.07% done, estimate finish Sun May 11 23:53:53 2008
 27.10% done, estimate finish Sun May 11 23:53:53 2008
 27.12% done, estimate finish Sun May 11 23:53:53 2008
 27.15% done, estimate finish Sun May 11 23:53:52 2008
 27.17% done, estimate finish Sun May 11 23:53:55 2008
 27.20% done, estimate finish Sun May 11 23:53:55 2008
 27.22% done, estimate finish Sun May 11 23:53:55 2008
 27.25% done, estimate finish Sun May 11 23:53:54 2008
 27.28% done, estimate finish Sun May 11 23:53:54 2008
 27.30% done, estimate finish Sun May 11 23:53:53 2008
 27.33% done, estimate finish Sun May 11 23:53:53 2008
 27.35% done, estimate finish Sun May 11 23:53:53 2008
 27.38% done, estimate finish Sun May 11 23:53:52 2008
 27.41% done, estimate finish Sun May 11 23:53:52 2008
 27.43% done, estimate finish Sun May 11 23:53:51 2008
 27.46% done, estimate finish Sun May 11 23:53:51 2008
 27.48% done, estimate finish Sun May 11 23:53:51 2008
 27.51% done, estimate finish Sun May 11 23:53:50 2008
 27.53% done, estimate finish Sun May 11 23:53:53 2008
 27.56% done, estimate finish Sun May 11 23:53:53 2008
 27.59% done, estimate finish Sun May 11 23:53:53 2008
 27.61% done, estimate finish Sun May 11 23:53:52 2008
 27.64% done, estimate finish Sun May 11 23:53:52 2008
 27.66% done, estimate finish Sun May 11 23:53:51 2008
 27.69% done, estimate finish Sun May 11 23:53:51 2008
 27.72% done, estimate finish Sun May 11 23:53:51 2008
 27.74% done, estimate finish Sun May 11 23:53:50 2008
 27.77% done, estimate finish Sun May 11 23:53:50 2008
 27.79% done, estimate finish Sun May 11 23:53:49 2008
 27.82% done, estimate finish Sun May 11 23:53:49 2008
 27.84% done, estimate finish Sun May 11 23:53:49 2008
 27.87% done, estimate finish Sun May 11 23:53:48 2008
 27.90% done, estimate finish Sun May 11 23:53:52 2008
 27.92% done, estimate finish Sun May 11 23:53:51 2008
 27.95% done, estimate finish Sun May 11 23:53:51 2008
 27.97% done, estimate finish Sun May 11 23:53:50 2008
 28.00% done, estimate finish Sun May 11 23:53:50 2008
 28.02% done, estimate finish Sun May 11 23:53:50 2008
 28.05% done, estimate finish Sun May 11 23:53:49 2008
 28.08% done, estimate finish Sun May 11 23:53:49 2008
 28.10% done, estimate finish Sun May 11 23:53:48 2008
 28.13% done, estimate finish Sun May 11 23:53:48 2008
 28.15% done, estimate finish Sun May 11 23:53:48 2008
 28.18% done, estimate finish Sun May 11 23:53:47 2008
 28.21% done, estimate finish Sun May 11 23:53:47 2008
 28.23% done, estimate finish Sun May 11 23:53:46 2008
 28.26% done, estimate finish Sun May 11 23:53:50 2008
 28.28% done, estimate finish Sun May 11 23:53:49 2008
 28.31% done, estimate finish Sun May 11 23:53:49 2008
 28.33% done, estimate finish Sun May 11 23:53:48 2008
 28.36% done, estimate finish Sun May 11 23:53:48 2008
 28.39% done, estimate finish Sun May 11 23:53:48 2008
 28.41% done, estimate finish Sun May 11 23:53:47 2008
 28.44% done, estimate finish Sun May 11 23:53:47 2008
 28.46% done, estimate finish Sun May 11 23:53:47 2008
 28.49% done, estimate finish Sun May 11 23:53:46 2008
 28.52% done, estimate finish Sun May 11 23:53:46 2008
 28.54% done, estimate finish Sun May 11 23:53:45 2008
 28.57% done, estimate finish Sun May 11 23:53:45 2008
 28.59% done, estimate finish Sun May 11 23:53:48 2008
 28.62% done, estimate finish Sun May 11 23:53:48 2008
 28.64% done, estimate finish Sun May 11 23:53:47 2008
 28.67% done, estimate finish Sun May 11 23:53:47 2008
 28.70% done, estimate finish Sun May 11 23:53:47 2008
 28.72% done, estimate finish Sun May 11 23:53:46 2008
 28.75% done, estimate finish Sun May 11 23:53:46 2008
 28.77% done, estimate finish Sun May 11 23:53:46 2008
 28.80% done, estimate finish Sun May 11 23:53:45 2008
 28.82% done, estimate finish Sun May 11 23:53:45 2008
 28.85% done, estimate finish Sun May 11 23:53:44 2008
 28.88% done, estimate finish Sun May 11 23:53:44 2008
 28.90% done, estimate finish Sun May 11 23:53:44 2008
 28.93% done, estimate finish Sun May 11 23:53:43 2008
 28.95% done, estimate finish Sun May 11 23:53:43 2008
 28.98% done, estimate finish Sun May 11 23:53:46 2008
 29.00% done, estimate finish Sun May 11 23:53:46 2008
 29.03% done, estimate finish Sun May 11 23:53:45 2008
 29.06% done, estimate finish Sun May 11 23:53:45 2008
 29.08% done, estimate finish Sun May 11 23:53:45 2008
 29.11% done, estimate finish Sun May 11 23:53:44 2008
 29.13% done, estimate finish Sun May 11 23:53:44 2008
 29.16% done, estimate finish Sun May 11 23:53:43 2008
 29.19% done, estimate finish Sun May 11 23:53:43 2008
 29.21% done, estimate finish Sun May 11 23:53:43 2008
 29.24% done, estimate finish Sun May 11 23:53:42 2008
 29.26% done, estimate finish Sun May 11 23:53:42 2008
 29.29% done, estimate finish Sun May 11 23:53:42 2008
 29.31% done, estimate finish Sun May 11 23:53:41 2008
 29.34% done, estimate finish Sun May 11 23:53:44 2008
 29.37% done, estimate finish Sun May 11 23:53:44 2008
 29.39% done, estimate finish Sun May 11 23:53:44 2008
 29.42% done, estimate finish Sun May 11 23:53:43 2008
 29.44% done, estimate finish Sun May 11 23:53:43 2008
 29.47% done, estimate finish Sun May 11 23:53:42 2008
 29.50% done, estimate finish Sun May 11 23:53:42 2008
 29.52% done, estimate finish Sun May 11 23:53:42 2008
 29.55% done, estimate finish Sun May 11 23:53:41 2008
 29.57% done, estimate finish Sun May 11 23:53:41 2008
 29.60% done, estimate finish Sun May 11 23:53:41 2008
 29.62% done, estimate finish Sun May 11 23:53:40 2008
 29.65% done, estimate finish Sun May 11 23:53:40 2008
 29.68% done, estimate finish Sun May 11 23:53:40 2008
 29.70% done, estimate finish Sun May 11 23:53:43 2008
 29.73% done, estimate finish Sun May 11 23:53:42 2008
 29.75% done, estimate finish Sun May 11 23:53:42 2008
 29.78% done, estimate finish Sun May 11 23:53:42 2008
 29.81% done, estimate finish Sun May 11 23:53:41 2008
 29.83% done, estimate finish Sun May 11 23:53:41 2008
 29.86% done, estimate finish Sun May 11 23:53:40 2008
 29.88% done, estimate finish Sun May 11 23:53:40 2008
 29.91% done, estimate finish Sun May 11 23:53:40 2008
 29.93% done, estimate finish Sun May 11 23:53:39 2008
 29.96% done, estimate finish Sun May 11 23:53:39 2008
 29.99% done, estimate finish Sun May 11 23:53:39 2008
 30.01% done, estimate finish Sun May 11 23:53:38 2008
 30.04% done, estimate finish Sun May 11 23:53:38 2008
 30.06% done, estimate finish Sun May 11 23:53:41 2008
 30.09% done, estimate finish Sun May 11 23:53:41 2008
 30.11% done, estimate finish Sun May 11 23:53:40 2008
 30.14% done, estimate finish Sun May 11 23:53:40 2008
 30.17% done, estimate finish Sun May 11 23:53:40 2008
 30.19% done, estimate finish Sun May 11 23:53:39 2008
 30.22% done, estimate finish Sun May 11 23:53:39 2008
 30.24% done, estimate finish Sun May 11 23:53:39 2008
 30.27% done, estimate finish Sun May 11 23:53:38 2008
 30.30% done, estimate finish Sun May 11 23:53:38 2008
 30.32% done, estimate finish Sun May 11 23:53:37 2008
 30.35% done, estimate finish Sun May 11 23:53:37 2008
 30.37% done, estimate finish Sun May 11 23:53:37 2008
 30.40% done, estimate finish Sun May 11 23:53:36 2008
 30.42% done, estimate finish Sun May 11 23:53:39 2008
 30.45% done, estimate finish Sun May 11 23:53:39 2008
 30.48% done, estimate finish Sun May 11 23:53:39 2008
 30.50% done, estimate finish Sun May 11 23:53:38 2008
 30.53% done, estimate finish Sun May 11 23:53:38 2008
 30.55% done, estimate finish Sun May 11 23:53:38 2008
 30.58% done, estimate finish Sun May 11 23:53:37 2008
 30.61% done, estimate finish Sun May 11 23:53:37 2008
 30.63% done, estimate finish Sun May 11 23:53:37 2008
 30.66% done, estimate finish Sun May 11 23:53:36 2008
 30.68% done, estimate finish Sun May 11 23:53:36 2008
 30.71% done, estimate finish Sun May 11 23:53:36 2008
 30.73% done, estimate finish Sun May 11 23:53:35 2008
 30.76% done, estimate finish Sun May 11 23:53:35 2008
 30.79% done, estimate finish Sun May 11 23:53:38 2008
 30.81% done, estimate finish Sun May 11 23:53:37 2008
 30.84% done, estimate finish Sun May 11 23:53:37 2008
 30.86% done, estimate finish Sun May 11 23:53:37 2008
 30.89% done, estimate finish Sun May 11 23:53:36 2008
 30.91% done, estimate finish Sun May 11 23:53:36 2008
 30.94% done, estimate finish Sun May 11 23:53:36 2008
 30.97% done, estimate finish Sun May 11 23:53:35 2008
 30.99% done, estimate finish Sun May 11 23:53:35 2008
 31.02% done, estimate finish Sun May 11 23:53:35 2008
 31.04% done, estimate finish Sun May 11 23:53:34 2008
 31.07% done, estimate finish Sun May 11 23:53:34 2008
 31.10% done, estimate finish Sun May 11 23:53:34 2008
 31.12% done, estimate finish Sun May 11 23:53:33 2008
 31.15% done, estimate finish Sun May 11 23:53:33 2008
 31.17% done, estimate finish Sun May 11 23:53:36 2008
 31.20% done, estimate finish Sun May 11 23:53:36 2008
 31.22% done, estimate finish Sun May 11 23:53:35 2008
 31.25% done, estimate finish Sun May 11 23:53:35 2008
 31.28% done, estimate finish Sun May 11 23:53:35 2008
 31.30% done, estimate finish Sun May 11 23:53:34 2008
 31.33% done, estimate finish Sun May 11 23:53:34 2008
 31.35% done, estimate finish Sun May 11 23:53:34 2008
 31.38% done, estimate finish Sun May 11 23:53:33 2008
 31.41% done, estimate finish Sun May 11 23:53:33 2008
 31.43% done, estimate finish Sun May 11 23:53:33 2008
 31.46% done, estimate finish Sun May 11 23:53:32 2008
 31.48% done, estimate finish Sun May 11 23:53:32 2008
 31.51% done, estimate finish Sun May 11 23:53:32 2008
 31.53% done, estimate finish Sun May 11 23:53:34 2008
 31.56% done, estimate finish Sun May 11 23:53:34 2008
 31.59% done, estimate finish Sun May 11 23:53:34 2008
 31.61% done, estimate finish Sun May 11 23:53:33 2008
 31.64% done, estimate finish Sun May 11 23:53:33 2008
 31.66% done, estimate finish Sun May 11 23:53:33 2008
 31.69% done, estimate finish Sun May 11 23:53:32 2008
 31.71% done, estimate finish Sun May 11 23:53:32 2008
 31.74% done, estimate finish Sun May 11 23:53:32 2008
 31.77% done, estimate finish Sun May 11 23:53:31 2008
 31.79% done, estimate finish Sun May 11 23:53:31 2008
 31.82% done, estimate finish Sun May 11 23:53:31 2008
 31.84% done, estimate finish Sun May 11 23:53:30 2008
 31.87% done, estimate finish Sun May 11 23:53:30 2008
 31.90% done, estimate finish Sun May 11 23:53:33 2008
 31.92% done, estimate finish Sun May 11 23:53:33 2008
 31.95% done, estimate finish Sun May 11 23:53:32 2008
 31.97% done, estimate finish Sun May 11 23:53:32 2008
 32.00% done, estimate finish Sun May 11 23:53:32 2008
 32.02% done, estimate finish Sun May 11 23:53:31 2008
 32.05% done, estimate finish Sun May 11 23:53:31 2008
 32.08% done, estimate finish Sun May 11 23:53:31 2008
 32.10% done, estimate finish Sun May 11 23:53:30 2008
 32.13% done, estimate finish Sun May 11 23:53:30 2008
 32.15% done, estimate finish Sun May 11 23:53:30 2008
 32.18% done, estimate finish Sun May 11 23:53:29 2008
 32.21% done, estimate finish Sun May 11 23:53:29 2008
 32.23% done, estimate finish Sun May 11 23:53:29 2008
 32.26% done, estimate finish Sun May 11 23:53:28 2008
 32.28% done, estimate finish Sun May 11 23:53:31 2008
 32.31% done, estimate finish Sun May 11 23:53:31 2008
 32.33% done, estimate finish Sun May 11 23:53:31 2008
 32.36% done, estimate finish Sun May 11 23:53:30 2008
 32.39% done, estimate finish Sun May 11 23:53:30 2008
 32.41% done, estimate finish Sun May 11 23:53:30 2008
 32.44% done, estimate finish Sun May 11 23:53:29 2008
 32.46% done, estimate finish Sun May 11 23:53:29 2008
 32.49% done, estimate finish Sun May 11 23:53:29 2008
 32.51% done, estimate finish Sun May 11 23:53:28 2008
 32.54% done, estimate finish Sun May 11 23:53:28 2008
 32.57% done, estimate finish Sun May 11 23:53:28 2008
 32.59% done, estimate finish Sun May 11 23:53:27 2008
 32.62% done, estimate finish Sun May 11 23:53:27 2008
 32.64% done, estimate finish Sun May 11 23:53:30 2008
 32.67% done, estimate finish Sun May 11 23:53:29 2008
 32.69% done, estimate finish Sun May 11 23:53:29 2008
 32.72% done, estimate finish Sun May 11 23:53:29 2008
 32.75% done, estimate finish Sun May 11 23:53:29 2008
 32.77% done, estimate finish Sun May 11 23:53:28 2008
 32.80% done, estimate finish Sun May 11 23:53:28 2008
 32.82% done, estimate finish Sun May 11 23:53:28 2008
 32.85% done, estimate finish Sun May 11 23:53:27 2008
 32.88% done, estimate finish Sun May 11 23:53:27 2008
 32.90% done, estimate finish Sun May 11 23:53:27 2008
 32.93% done, estimate finish Sun May 11 23:53:26 2008
 32.95% done, estimate finish Sun May 11 23:53:26 2008
 32.98% done, estimate finish Sun May 11 23:53:26 2008
 33.00% done, estimate finish Sun May 11 23:53:25 2008
 33.03% done, estimate finish Sun May 11 23:53:28 2008
 33.06% done, estimate finish Sun May 11 23:53:28 2008
 33.08% done, estimate finish Sun May 11 23:53:28 2008
 33.11% done, estimate finish Sun May 11 23:53:27 2008
 33.13% done, estimate finish Sun May 11 23:53:27 2008
 33.16% done, estimate finish Sun May 11 23:53:27 2008
 33.19% done, estimate finish Sun May 11 23:53:26 2008
 33.21% done, estimate finish Sun May 11 23:53:26 2008
 33.24% done, estimate finish Sun May 11 23:53:26 2008
 33.26% done, estimate finish Sun May 11 23:53:25 2008
 33.29% done, estimate finish Sun May 11 23:53:25 2008
 33.31% done, estimate finish Sun May 11 23:53:25 2008
 33.34% done, estimate finish Sun May 11 23:53:24 2008
 33.37% done, estimate finish Sun May 11 23:53:24 2008
 33.39% done, estimate finish Sun May 11 23:53:24 2008
 33.42% done, estimate finish Sun May 11 23:53:26 2008
 33.44% done, estimate finish Sun May 11 23:53:26 2008
 33.47% done, estimate finish Sun May 11 23:53:26 2008
 33.50% done, estimate finish Sun May 11 23:53:26 2008
 33.52% done, estimate finish Sun May 11 23:53:25 2008
 33.55% done, estimate finish Sun May 11 23:53:25 2008
 33.57% done, estimate finish Sun May 11 23:53:25 2008
 33.60% done, estimate finish Sun May 11 23:53:24 2008
 33.62% done, estimate finish Sun May 11 23:53:24 2008
 33.65% done, estimate finish Sun May 11 23:53:24 2008
 33.68% done, estimate finish Sun May 11 23:53:23 2008
 33.70% done, estimate finish Sun May 11 23:53:23 2008
 33.73% done, estimate finish Sun May 11 23:53:23 2008
 33.75% done, estimate finish Sun May 11 23:53:23 2008
 33.78% done, estimate finish Sun May 11 23:53:25 2008
 33.80% done, estimate finish Sun May 11 23:53:25 2008
 33.83% done, estimate finish Sun May 11 23:53:25 2008
 33.86% done, estimate finish Sun May 11 23:53:24 2008
 33.88% done, estimate finish Sun May 11 23:53:24 2008
 33.91% done, estimate finish Sun May 11 23:53:24 2008
 33.93% done, estimate finish Sun May 11 23:53:23 2008
 33.96% done, estimate finish Sun May 11 23:53:23 2008
 33.99% done, estimate finish Sun May 11 23:53:23 2008
 34.01% done, estimate finish Sun May 11 23:53:22 2008
 34.04% done, estimate finish Sun May 11 23:53:22 2008
 34.06% done, estimate finish Sun May 11 23:53:22 2008
 34.09% done, estimate finish Sun May 11 23:53:22 2008
 34.11% done, estimate finish Sun May 11 23:53:21 2008
 34.14% done, estimate finish Sun May 11 23:53:21 2008
 34.17% done, estimate finish Sun May 11 23:53:24 2008
 34.19% done, estimate finish Sun May 11 23:53:23 2008
 34.22% done, estimate finish Sun May 11 23:53:23 2008
 34.24% done, estimate finish Sun May 11 23:53:23 2008
 34.27% done, estimate finish Sun May 11 23:53:22 2008
 34.30% done, estimate finish Sun May 11 23:53:22 2008
 34.32% done, estimate finish Sun May 11 23:53:22 2008
 34.35% done, estimate finish Sun May 11 23:53:22 2008
 34.37% done, estimate finish Sun May 11 23:53:21 2008
 34.40% done, estimate finish Sun May 11 23:53:21 2008
 34.42% done, estimate finish Sun May 11 23:53:21 2008
 34.45% done, estimate finish Sun May 11 23:53:20 2008
 34.48% done, estimate finish Sun May 11 23:53:20 2008
 34.50% done, estimate finish Sun May 11 23:53:20 2008
 34.53% done, estimate finish Sun May 11 23:53:19 2008
 34.55% done, estimate finish Sun May 11 23:53:22 2008
 34.58% done, estimate finish Sun May 11 23:53:22 2008
 34.60% done, estimate finish Sun May 11 23:53:22 2008
 34.63% done, estimate finish Sun May 11 23:53:21 2008
 34.66% done, estimate finish Sun May 11 23:53:21 2008
 34.68% done, estimate finish Sun May 11 23:53:21 2008
 34.71% done, estimate finish Sun May 11 23:53:20 2008
 34.73% done, estimate finish Sun May 11 23:53:20 2008
 34.76% done, estimate finish Sun May 11 23:53:20 2008
 34.79% done, estimate finish Sun May 11 23:53:19 2008
 34.81% done, estimate finish Sun May 11 23:53:19 2008
 34.84% done, estimate finish Sun May 11 23:53:19 2008
 34.86% done, estimate finish Sun May 11 23:53:19 2008
 34.89% done, estimate finish Sun May 11 23:53:18 2008
 34.91% done, estimate finish Sun May 11 23:53:18 2008
 34.94% done, estimate finish Sun May 11 23:53:21 2008
 34.97% done, estimate finish Sun May 11 23:53:20 2008
 34.99% done, estimate finish Sun May 11 23:53:20 2008
 35.02% done, estimate finish Sun May 11 23:53:20 2008
 35.04% done, estimate finish Sun May 11 23:53:19 2008
 35.07% done, estimate finish Sun May 11 23:53:19 2008
 35.10% done, estimate finish Sun May 11 23:53:19 2008
 35.12% done, estimate finish Sun May 11 23:53:19 2008
 35.15% done, estimate finish Sun May 11 23:53:18 2008
 35.17% done, estimate finish Sun May 11 23:53:18 2008
 35.20% done, estimate finish Sun May 11 23:53:18 2008
 35.22% done, estimate finish Sun May 11 23:53:17 2008
 35.25% done, estimate finish Sun May 11 23:53:17 2008
 35.28% done, estimate finish Sun May 11 23:53:17 2008
 35.30% done, estimate finish Sun May 11 23:53:19 2008
 35.33% done, estimate finish Sun May 11 23:53:19 2008
 35.35% done, estimate finish Sun May 11 23:53:19 2008
 35.38% done, estimate finish Sun May 11 23:53:19 2008
 35.41% done, estimate finish Sun May 11 23:53:18 2008
 35.43% done, estimate finish Sun May 11 23:53:18 2008
 35.46% done, estimate finish Sun May 11 23:53:18 2008
 35.48% done, estimate finish Sun May 11 23:53:17 2008
 35.51% done, estimate finish Sun May 11 23:53:17 2008
 35.53% done, estimate finish Sun May 11 23:53:17 2008
 35.56% done, estimate finish Sun May 11 23:53:17 2008
 35.59% done, estimate finish Sun May 11 23:53:16 2008
 35.61% done, estimate finish Sun May 11 23:53:16 2008
 35.64% done, estimate finish Sun May 11 23:53:16 2008
 35.66% done, estimate finish Sun May 11 23:53:15 2008
 35.69% done, estimate finish Sun May 11 23:53:18 2008
 35.71% done, estimate finish Sun May 11 23:53:18 2008
 35.74% done, estimate finish Sun May 11 23:53:17 2008
 35.77% done, estimate finish Sun May 11 23:53:17 2008
 35.79% done, estimate finish Sun May 11 23:53:17 2008
 35.82% done, estimate finish Sun May 11 23:53:17 2008
 35.84% done, estimate finish Sun May 11 23:53:16 2008
 35.87% done, estimate finish Sun May 11 23:53:16 2008
 35.89% done, estimate finish Sun May 11 23:53:16 2008
 35.92% done, estimate finish Sun May 11 23:53:15 2008
 35.95% done, estimate finish Sun May 11 23:53:15 2008
 35.97% done, estimate finish Sun May 11 23:53:15 2008
 36.00% done, estimate finish Sun May 11 23:53:15 2008
 36.02% done, estimate finish Sun May 11 23:53:14 2008
 36.05% done, estimate finish Sun May 11 23:53:14 2008
 36.08% done, estimate finish Sun May 11 23:53:17 2008
 36.10% done, estimate finish Sun May 11 23:53:16 2008
 36.13% done, estimate finish Sun May 11 23:53:16 2008
 36.15% done, estimate finish Sun May 11 23:53:16 2008
 36.18% done, estimate finish Sun May 11 23:53:15 2008
 36.20% done, estimate finish Sun May 11 23:53:15 2008
 36.23% done, estimate finish Sun May 11 23:53:15 2008
 36.26% done, estimate finish Sun May 11 23:53:15 2008
 36.28% done, estimate finish Sun May 11 23:53:14 2008
 36.31% done, estimate finish Sun May 11 23:53:14 2008
 36.33% done, estimate finish Sun May 11 23:53:14 2008
 36.36% done, estimate finish Sun May 11 23:53:14 2008
 36.39% done, estimate finish Sun May 11 23:53:13 2008
 36.41% done, estimate finish Sun May 11 23:53:13 2008
 36.44% done, estimate finish Sun May 11 23:53:13 2008
 36.46% done, estimate finish Sun May 11 23:53:15 2008
 36.49% done, estimate finish Sun May 11 23:53:15 2008
 36.51% done, estimate finish Sun May 11 23:53:15 2008
 36.54% done, estimate finish Sun May 11 23:53:14 2008
 36.57% done, estimate finish Sun May 11 23:53:14 2008
 36.59% done, estimate finish Sun May 11 23:53:14 2008
 36.62% done, estimate finish Sun May 11 23:53:14 2008
 36.64% done, estimate finish Sun May 11 23:53:13 2008
 36.67% done, estimate finish Sun May 11 23:53:13 2008
 36.70% done, estimate finish Sun May 11 23:53:13 2008
 36.72% done, estimate finish Sun May 11 23:53:12 2008
 36.75% done, estimate finish Sun May 11 23:53:12 2008
 36.77% done, estimate finish Sun May 11 23:53:12 2008
 36.80% done, estimate finish Sun May 11 23:53:12 2008
 36.82% done, estimate finish Sun May 11 23:53:11 2008
 36.85% done, estimate finish Sun May 11 23:53:14 2008
 36.88% done, estimate finish Sun May 11 23:53:14 2008
 36.90% done, estimate finish Sun May 11 23:53:13 2008
 36.93% done, estimate finish Sun May 11 23:53:13 2008
 36.95% done, estimate finish Sun May 11 23:53:13 2008
 36.98% done, estimate finish Sun May 11 23:53:13 2008
 37.00% done, estimate finish Sun May 11 23:53:12 2008
 37.03% done, estimate finish Sun May 11 23:53:12 2008
 37.06% done, estimate finish Sun May 11 23:53:12 2008
 37.08% done, estimate finish Sun May 11 23:53:11 2008
 37.11% done, estimate finish Sun May 11 23:53:11 2008
 37.13% done, estimate finish Sun May 11 23:53:11 2008
 37.16% done, estimate finish Sun May 11 23:53:11 2008
 37.19% done, estimate finish Sun May 11 23:53:10 2008
 37.21% done, estimate finish Sun May 11 23:53:10 2008
 37.24% done, estimate finish Sun May 11 23:53:13 2008
 37.26% done, estimate finish Sun May 11 23:53:12 2008
 37.29% done, estimate finish Sun May 11 23:53:12 2008
 37.31% done, estimate finish Sun May 11 23:53:12 2008
 37.34% done, estimate finish Sun May 11 23:53:11 2008
 37.37% done, estimate finish Sun May 11 23:53:11 2008
 37.39% done, estimate finish Sun May 11 23:53:11 2008
 37.42% done, estimate finish Sun May 11 23:53:11 2008
 37.44% done, estimate finish Sun May 11 23:53:10 2008
 37.47% done, estimate finish Sun May 11 23:53:10 2008
 37.50% done, estimate finish Sun May 11 23:53:10 2008
 37.52% done, estimate finish Sun May 11 23:53:10 2008
 37.55% done, estimate finish Sun May 11 23:53:09 2008
 37.57% done, estimate finish Sun May 11 23:53:09 2008
 37.60% done, estimate finish Sun May 11 23:53:09 2008
 37.62% done, estimate finish Sun May 11 23:53:11 2008
 37.65% done, estimate finish Sun May 11 23:53:11 2008
 37.68% done, estimate finish Sun May 11 23:53:11 2008
 37.70% done, estimate finish Sun May 11 23:53:10 2008
 37.73% done, estimate finish Sun May 11 23:53:10 2008
 37.75% done, estimate finish Sun May 11 23:53:10 2008
 37.78% done, estimate finish Sun May 11 23:53:10 2008
 37.81% done, estimate finish Sun May 11 23:53:09 2008
 37.83% done, estimate finish Sun May 11 23:53:09 2008
 37.86% done, estimate finish Sun May 11 23:53:09 2008
 37.88% done, estimate finish Sun May 11 23:53:09 2008
 37.91% done, estimate finish Sun May 11 23:53:08 2008
 37.93% done, estimate finish Sun May 11 23:53:08 2008
 37.96% done, estimate finish Sun May 11 23:53:08 2008
 37.99% done, estimate finish Sun May 11 23:53:08 2008
 38.01% done, estimate finish Sun May 11 23:53:07 2008
 38.04% done, estimate finish Sun May 11 23:53:10 2008
 38.06% done, estimate finish Sun May 11 23:53:09 2008
 38.09% done, estimate finish Sun May 11 23:53:09 2008
 38.11% done, estimate finish Sun May 11 23:53:09 2008
 38.14% done, estimate finish Sun May 11 23:53:09 2008
 38.17% done, estimate finish Sun May 11 23:53:08 2008
 38.19% done, estimate finish Sun May 11 23:53:08 2008
 38.22% done, estimate finish Sun May 11 23:53:08 2008
 38.24% done, estimate finish Sun May 11 23:53:08 2008
 38.27% done, estimate finish Sun May 11 23:53:07 2008
 38.30% done, estimate finish Sun May 11 23:53:07 2008
 38.32% done, estimate finish Sun May 11 23:53:07 2008
 38.35% done, estimate finish Sun May 11 23:53:07 2008
 38.37% done, estimate finish Sun May 11 23:53:06 2008
 38.40% done, estimate finish Sun May 11 23:53:06 2008
 38.42% done, estimate finish Sun May 11 23:53:08 2008
 38.45% done, estimate finish Sun May 11 23:53:08 2008
 38.48% done, estimate finish Sun May 11 23:53:08 2008
 38.50% done, estimate finish Sun May 11 23:53:08 2008
 38.53% done, estimate finish Sun May 11 23:53:07 2008
 38.55% done, estimate finish Sun May 11 23:53:07 2008
 38.58% done, estimate finish Sun May 11 23:53:07 2008
 38.60% done, estimate finish Sun May 11 23:53:07 2008
 38.63% done, estimate finish Sun May 11 23:53:06 2008
 38.66% done, estimate finish Sun May 11 23:53:06 2008
 38.68% done, estimate finish Sun May 11 23:53:06 2008
 38.71% done, estimate finish Sun May 11 23:53:06 2008
 38.73% done, estimate finish Sun May 11 23:53:05 2008
 38.76% done, estimate finish Sun May 11 23:53:05 2008
 38.78% done, estimate finish Sun May 11 23:53:05 2008
 38.81% done, estimate finish Sun May 11 23:53:07 2008
 38.84% done, estimate finish Sun May 11 23:53:07 2008
 38.86% done, estimate finish Sun May 11 23:53:07 2008
 38.89% done, estimate finish Sun May 11 23:53:07 2008
 38.91% done, estimate finish Sun May 11 23:53:06 2008
 38.94% done, estimate finish Sun May 11 23:53:06 2008
 38.97% done, estimate finish Sun May 11 23:53:06 2008
 38.99% done, estimate finish Sun May 11 23:53:06 2008
 39.02% done, estimate finish Sun May 11 23:53:05 2008
 39.04% done, estimate finish Sun May 11 23:53:05 2008
 39.07% done, estimate finish Sun May 11 23:53:05 2008
 39.09% done, estimate finish Sun May 11 23:53:05 2008
 39.12% done, estimate finish Sun May 11 23:53:04 2008
 39.15% done, estimate finish Sun May 11 23:53:04 2008
 39.17% done, estimate finish Sun May 11 23:53:04 2008
 39.20% done, estimate finish Sun May 11 23:53:04 2008
 39.22% done, estimate finish Sun May 11 23:53:06 2008
 39.25% done, estimate finish Sun May 11 23:53:06 2008
 39.28% done, estimate finish Sun May 11 23:53:05 2008
 39.30% done, estimate finish Sun May 11 23:53:05 2008
 39.33% done, estimate finish Sun May 11 23:53:05 2008
 39.35% done, estimate finish Sun May 11 23:53:05 2008
 39.38% done, estimate finish Sun May 11 23:53:04 2008
 39.40% done, estimate finish Sun May 11 23:53:04 2008
 39.43% done, estimate finish Sun May 11 23:53:04 2008
 39.46% done, estimate finish Sun May 11 23:53:04 2008
 39.48% done, estimate finish Sun May 11 23:53:03 2008
 39.51% done, estimate finish Sun May 11 23:53:03 2008
 39.53% done, estimate finish Sun May 11 23:53:03 2008
 39.56% done, estimate finish Sun May 11 23:53:03 2008
 39.59% done, estimate finish Sun May 11 23:53:02 2008
 39.61% done, estimate finish Sun May 11 23:53:05 2008
 39.64% done, estimate finish Sun May 11 23:53:04 2008
 39.66% done, estimate finish Sun May 11 23:53:04 2008
 39.69% done, estimate finish Sun May 11 23:53:04 2008
 39.71% done, estimate finish Sun May 11 23:53:04 2008
 39.74% done, estimate finish Sun May 11 23:53:03 2008
 39.77% done, estimate finish Sun May 11 23:53:03 2008
 39.79% done, estimate finish Sun May 11 23:53:03 2008
 39.82% done, estimate finish Sun May 11 23:53:03 2008
 39.84% done, estimate finish Sun May 11 23:53:02 2008
 39.87% done, estimate finish Sun May 11 23:53:02 2008
 39.89% done, estimate finish Sun May 11 23:53:04 2008
 39.92% done, estimate finish Sun May 11 23:53:04 2008
 39.95% done, estimate finish Sun May 11 23:53:04 2008
 39.97% done, estimate finish Sun May 11 23:53:04 2008
 40.00% done, estimate finish Sun May 11 23:53:04 2008
 40.02% done, estimate finish Sun May 11 23:53:03 2008
 40.05% done, estimate finish Sun May 11 23:53:03 2008
 40.08% done, estimate finish Sun May 11 23:53:03 2008
 40.10% done, estimate finish Sun May 11 23:53:03 2008
 40.13% done, estimate finish Sun May 11 23:53:02 2008
 40.15% done, estimate finish Sun May 11 23:53:02 2008
 40.18% done, estimate finish Sun May 11 23:53:02 2008
 40.20% done, estimate finish Sun May 11 23:53:02 2008
 40.23% done, estimate finish Sun May 11 23:53:01 2008
 40.26% done, estimate finish Sun May 11 23:53:01 2008
 40.28% done, estimate finish Sun May 11 23:53:01 2008
 40.31% done, estimate finish Sun May 11 23:53:01 2008
 40.33% done, estimate finish Sun May 11 23:53:00 2008
 40.36% done, estimate finish Sun May 11 23:53:00 2008
 40.39% done, estimate finish Sun May 11 23:53:00 2008
 40.41% done, estimate finish Sun May 11 23:53:02 2008
 40.44% done, estimate finish Sun May 11 23:53:02 2008
 40.46% done, estimate finish Sun May 11 23:53:02 2008
 40.49% done, estimate finish Sun May 11 23:53:01 2008
 40.51% done, estimate finish Sun May 11 23:53:01 2008
 40.54% done, estimate finish Sun May 11 23:53:01 2008
 40.57% done, estimate finish Sun May 11 23:53:01 2008
 40.59% done, estimate finish Sun May 11 23:53:00 2008
 40.62% done, estimate finish Sun May 11 23:53:00 2008
 40.64% done, estimate finish Sun May 11 23:53:00 2008
 40.67% done, estimate finish Sun May 11 23:53:00 2008
 40.70% done, estimate finish Sun May 11 23:53:00 2008
 40.72% done, estimate finish Sun May 11 23:52:59 2008
 40.75% done, estimate finish Sun May 11 23:52:59 2008
 40.77% done, estimate finish Sun May 11 23:52:59 2008
 40.80% done, estimate finish Sun May 11 23:53:01 2008
 40.82% done, estimate finish Sun May 11 23:53:01 2008
 40.85% done, estimate finish Sun May 11 23:53:01 2008
 40.88% done, estimate finish Sun May 11 23:53:00 2008
 40.90% done, estimate finish Sun May 11 23:53:00 2008
 40.93% done, estimate finish Sun May 11 23:53:00 2008
 40.95% done, estimate finish Sun May 11 23:53:00 2008
 40.98% done, estimate finish Sun May 11 23:52:59 2008
 41.00% done, estimate finish Sun May 11 23:52:59 2008
 41.03% done, estimate finish Sun May 11 23:52:59 2008
 41.06% done, estimate finish Sun May 11 23:52:59 2008
 41.08% done, estimate finish Sun May 11 23:52:58 2008
 41.11% done, estimate finish Sun May 11 23:52:58 2008
 41.13% done, estimate finish Sun May 11 23:52:58 2008
 41.16% done, estimate finish Sun May 11 23:52:58 2008
 41.19% done, estimate finish Sun May 11 23:52:58 2008
 41.21% done, estimate finish Sun May 11 23:53:00 2008
 41.24% done, estimate finish Sun May 11 23:53:00 2008
 41.26% done, estimate finish Sun May 11 23:52:59 2008
 41.29% done, estimate finish Sun May 11 23:52:59 2008
 41.31% done, estimate finish Sun May 11 23:52:59 2008
 41.34% done, estimate finish Sun May 11 23:52:59 2008
 41.37% done, estimate finish Sun May 11 23:52:58 2008
 41.39% done, estimate finish Sun May 11 23:52:58 2008
 41.42% done, estimate finish Sun May 11 23:52:58 2008
 41.44% done, estimate finish Sun May 11 23:52:58 2008
 41.47% done, estimate finish Sun May 11 23:52:57 2008
 41.50% done, estimate finish Sun May 11 23:52:57 2008
 41.52% done, estimate finish Sun May 11 23:52:57 2008
 41.55% done, estimate finish Sun May 11 23:52:57 2008
 41.57% done, estimate finish Sun May 11 23:52:57 2008
 41.60% done, estimate finish Sun May 11 23:52:59 2008
 41.62% done, estimate finish Sun May 11 23:52:58 2008
 41.65% done, estimate finish Sun May 11 23:52:58 2008
 41.68% done, estimate finish Sun May 11 23:53:00 2008
 41.70% done, estimate finish Sun May 11 23:53:03 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid generic_database -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /home/mdutku/tmp/kde-mdutku/k3bQE38bb.tmp -rational-rock -hide-list /home/mdutku/tmp/kde-mdutku/k3bZa7l2b.tmp -joliet -joliet-long -hide-joliet-list /home/mdutku/tmp/kde-mdutku/k3b5y2j2a.tmp -no-cache-inodes -full-iso9660-filenames -disable-deep-relocation -iso-level 2 -path-list /home/mdutku/tmp/kde-mdutku/k3bXjbLic.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid generic_database -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /home/mdutku/tmp/kde-mdutku/k3bQyGeHa.tmp -rational-rock -hide-list /home/mdutku/tmp/kde-mdutku/k3bg7P1kb.tmp -joliet -joliet-long -hide-joliet-list /home/mdutku/tmp/kde-mdutku/k3bFAG4Ta.tmp -no-cache-inodes -full-iso9660-filenames -disable-deep-relocation -iso-level 2 -path-list /home/mdutku/tmp/kde-mdutku/k3b67jmfc.tmp 
```

---

### Post by AdamWill on 2008-05-14
So the same thing happens on both Ubuntu and Mandriva?

Can you check /var/log/messages right after it fails and see if there's any useful error message there? There's really nothing in the log you posted, it just suddenly cuts off halfway through the normal writing process with no apparent error message.

Thanks!

---

### Post by dca on 2008-05-16
See if you can drop the write speed to 4x and try again...

---

### Post by &amp;wP*!) on 2008-05-17
> **AdamWill]So the same thing happens on both Ubuntu and Mandriva?[/QUOTE]
Yes. Also on Fedora and OpenSUSE. From now on all messages belong to a Mandriva Session.
[LIST]
[*]Mandriva version is:```
Linux localhost 2.6.24.4-desktop-1mnb #1 SMP Thu Mar 27 14:34:39 CET 2008 i686 AMD Athlon(tm) XP 2800+ GNU/Linux
```
[*]K3B is 1.0.4.
[*]Mainboard: MSI MS-6590
[*]DVD Writer: LG GH20NS10 20x DVD+R write speed
[*]media: Philips DVD+R 16x DVD+R write speed
[*]OS resides on /dev/hdd
[*]data to be written reside on /dev/hda and on NTFS filesystem
[/LIST]
[QUOTE=AdamWill]Can you check /var/log/messages right after it fails and see if there's any useful error message there? There's really nothing in the log you posted, it just suddenly cuts off halfway through the normal writing process with no apparent error message.[/QUOTE]
The first messages about the SATA DVD Writer is as follows:
```
May 17 09:38:10 localhost kernel: SCSI subsystem initialized                                         
May 17 09:38:10 localhost kernel: ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 17                                                                                                    
May 17 09:38:10 localhost kernel: sata_via 0000:00:0f.0: routed to hard irq line 10
May 17 09:38:10 localhost kernel: scsi0 : sata_via                                                   
May 17 09:38:10 localhost kernel: scsi1 : sata_via                                                   
May 17 09:38:10 localhost kernel: ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 17
May 17 09:38:10 localhost kernel: ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 17
May 17 09:38:10 localhost kernel: ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
May 17 09:38:10 localhost kernel: ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 17 09:38:10 localhost kernel: ata2.00: ATAPI: HL-DT-ST DVDRAM GH20NS10, EL00, max UDMA/100       
May 17 09:38:10 localhost kernel: ata2.00: configured for UDMA/100                                   
May 17 09:38:10 localhost kernel: scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH20NS10  EL00 PQ: 0 ANSI: 5
...
May 17 09:38:10 localhost kernel: Driver 'sr' needs updating - please use bus_type methods
May 17 09:38:10 localhost kernel: sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May 17 09:38:10 localhost kernel: sr 1:0:0:0: Attached scsi generic sg0 type 5


```
[QUOTE=dca said:**
> See if you can drop the write speed to 4x and try again...
I have now tried to burn a DVD+R with 4x.

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24.4-desktop-1mnb
Devices
-----------------------
HL-DT-ST DVDRAM GH20NS10 EL00 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

SAMSUNG CDRW/DVD SM-352B T809 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]
Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 1937608 (3968221184 bytes)
Pipe throughput: 3968221184 bytes read, 3968221184 bytes written.

Used versions
-----------------------
mkisofs: 1.1.7.1
growisofs: 7.0

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 4.1x1352KBps.
          0/3968221184 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3968221184 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3968221184 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
   13893632/3968221184 ( 0.4%) @3.0x, remaining 66:24 RBU 100.0% UBU   2.9%
   32342016/3968221184 ( 0.8%) @4.0x, remaining 36:30 RBU 100.0% UBU 100.0%
   50823168/3968221184 ( 1.3%) @4.0x, remaining 26:58 RBU 100.0% UBU 100.0%
   69271552/3968221184 ( 1.7%) @4.0x, remaining 22:30 RBU 100.0% UBU 100.0%
   87719936/3968221184 ( 2.2%) @4.0x, remaining 20:38 RBU 100.0% UBU 100.0%
  106201088/3968221184 ( 2.7%) @4.0x, remaining 18:47 RBU 100.0% UBU 100.0%
  124649472/3968221184 ( 3.1%) @4.0x, remaining 17:28 RBU 100.0% UBU 100.0%
  143130624/3968221184 ( 3.6%) @4.0x, remaining 16:55 RBU 100.0% UBU 100.0%
  161579008/3968221184 ( 4.1%) @4.0x, remaining 16:05 RBU 100.0% UBU 100.0%
  180060160/3968221184 ( 4.5%) @4.0x, remaining 15:25 RBU 100.0% UBU 100.0%
  198508544/3968221184 ( 5.0%) @4.0x, remaining 15:11 RBU 100.0% UBU 100.0%
  216989696/3968221184 ( 5.5%) @4.0x, remaining 14:41 RBU 100.0% UBU 100.0%
  235438080/3968221184 ( 5.9%) @4.0x, remaining 14:16 RBU 100.0% UBU 100.0%
  253919232/3968221184 ( 6.4%) @4.0x, remaining 14:08 RBU 100.0% UBU 100.0%
  272367616/3968221184 ( 6.9%) @4.0x, remaining 13:47 RBU 100.0% UBU 100.0%
  290848768/3968221184 ( 7.3%) @4.0x, remaining 13:29 RBU 100.0% UBU 100.0%
  309297152/3968221184 ( 7.8%) @4.0x, remaining 13:24 RBU 100.0% UBU 100.0%
  327778304/3968221184 ( 8.3%) @4.0x, remaining 13:08 RBU 100.0% UBU 100.0%
  346226688/3968221184 ( 8.7%) @4.0x, remaining 12:54 RBU 100.0% UBU 100.0%
  364707840/3968221184 ( 9.2%) @4.0x, remaining 12:50 RBU 100.0% UBU 100.0%
  383188992/3968221184 ( 9.7%) @4.0x, remaining 12:37 RBU 100.0% UBU 100.0%
  401637376/3968221184 (10.1%) @4.0x, remaining 12:25 RBU 100.0% UBU 100.0%
  420118528/3968221184 (10.6%) @4.0x, remaining 12:23 RBU 100.0% UBU 100.0%
  438566912/3968221184 (11.1%) @4.0x, remaining 12:12 RBU 100.0% UBU 100.0%
  457048064/3968221184 (11.5%) @4.0x, remaining 12:02 RBU 100.0% UBU 100.0%
  475529216/3968221184 (12.0%) @4.0x, remaining 11:59 RBU 100.0% UBU 100.0%
  493977600/3968221184 (12.4%) @4.0x, remaining 11:50 RBU 100.0% UBU 100.0%
  512458752/3968221184 (12.9%) @4.0x, remaining 11:41 RBU 100.0% UBU 100.0%
  530907136/3968221184 (13.4%) @4.0x, remaining 11:39 RBU 100.0% UBU 100.0%
  549388288/3968221184 (13.8%) @4.0x, remaining 11:30 RBU 100.0% UBU 100.0%
  567869440/3968221184 (14.3%) @4.0x, remaining 11:22 RBU 100.0% UBU 100.0%
  586317824/3968221184 (14.8%) @4.0x, remaining 11:20 RBU 100.0% UBU 100.0%
  604798976/3968221184 (15.2%) @4.0x, remaining 11:12 RBU 100.0% UBU 100.0%
  623247360/3968221184 (15.7%) @4.0x, remaining 11:05 RBU 100.0% UBU 100.0%
  641728512/3968221184 (16.2%) @4.0x, remaining 11:03 RBU 100.0% UBU 100.0%
  660209664/3968221184 (16.6%) @4.0x, remaining 10:56 RBU 100.0% UBU 100.0%
  678658048/3968221184 (17.1%) @4.0x, remaining 10:49 RBU 100.0% UBU 100.0%
  697139200/3968221184 (17.6%) @4.0x, remaining 10:47 RBU 100.0% UBU 100.0%
  715620352/3968221184 (18.0%) @4.0x, remaining 10:40 RBU 100.0% UBU 100.0%
  734068736/3968221184 (18.5%) @4.0x, remaining 10:34 RBU 100.0% UBU 100.0%
  752549888/3968221184 (19.0%) @4.0x, remaining 10:32 RBU 100.0% UBU 100.0%
  771031040/3968221184 (19.4%) @4.0x, remaining 10:26 RBU 100.0% UBU 100.0%
  789479424/3968221184 (19.9%) @4.0x, remaining 10:20 RBU 100.0% UBU 100.0%
  807960576/3968221184 (20.4%) @4.0x, remaining 10:18 RBU 100.0% UBU 100.0%
  826441728/3968221184 (20.8%) @4.0x, remaining 10:12 RBU 100.0% UBU 100.0%
  844922880/3968221184 (21.3%) @4.0x, remaining 10:06 RBU 100.0% UBU 100.0%
  863371264/3968221184 (21.8%) @4.0x, remaining 10:04 RBU 100.0% UBU 100.0%
  881852416/3968221184 (22.2%) @4.0x, remaining 9:58 RBU 100.0% UBU 100.0%
  900333568/3968221184 (22.7%) @4.0x, remaining 9:52 RBU 100.0% UBU 100.0%
  918781952/3968221184 (23.2%) @4.0x, remaining 9:50 RBU 100.0% UBU 100.0%
  937263104/3968221184 (23.6%) @4.0x, remaining 9:45 RBU 100.0% UBU 100.0%
  955744256/3968221184 (24.1%) @4.0x, remaining 9:39 RBU 100.0% UBU 100.0%
  974225408/3968221184 (24.6%) @4.0x, remaining 9:37 RBU 100.0% UBU 100.0%
  992673792/3968221184 (25.0%) @4.0x, remaining 9:32 RBU 100.0% UBU 100.0%
 1011154944/3968221184 (25.5%) @4.0x, remaining 9:27 RBU 100.0% UBU 100.0%
 1029636096/3968221184 (25.9%) @4.0x, remaining 9:25 RBU 100.0% UBU 100.0%
 1048117248/3968221184 (26.4%) @4.0x, remaining 9:19 RBU 100.0% UBU 100.0%
 1066565632/3968221184 (26.9%) @4.0x, remaining 9:14 RBU 100.0% UBU 100.0%
 1085046784/3968221184 (27.3%) @4.0x, remaining 9:12 RBU 100.0% UBU 100.0%
 1103527936/3968221184 (27.8%) @4.0x, remaining 9:07 RBU 100.0% UBU 100.0%
 1122009088/3968221184 (28.3%) @4.0x, remaining 9:02 RBU 100.0% UBU 100.0%
 1140490240/3968221184 (28.7%) @4.0x, remaining 9:00 RBU 100.0% UBU 100.0%
 1158938624/3968221184 (29.2%) @4.0x, remaining 8:55 RBU 100.0% UBU 100.0%
 1177419776/3968221184 (29.7%) @4.0x, remaining 8:50 RBU 100.0% UBU 100.0%
 1195900928/3968221184 (30.1%) @4.0x, remaining 8:48 RBU 100.0% UBU 100.0%
 1214382080/3968221184 (30.6%) @4.0x, remaining 8:43 RBU 100.0% UBU 100.0%
 1232830464/3968221184 (31.1%) @4.0x, remaining 8:39 RBU 100.0% UBU 100.0%
 1251311616/3968221184 (31.5%) @4.0x, remaining 8:36 RBU 100.0% UBU 100.0%
 1269792768/3968221184 (32.0%) @4.0x, remaining 8:32 RBU 100.0% UBU 100.0%
 1288273920/3968221184 (32.5%) @4.0x, remaining 8:27 RBU 100.0% UBU 100.0%
 1306755072/3968221184 (32.9%) @4.0x, remaining 8:25 RBU 100.0% UBU 100.0%
 1325203456/3968221184 (33.4%) @4.0x, remaining 8:20 RBU 100.0% UBU 100.0%
 1343684608/3968221184 (33.9%) @4.0x, remaining 8:16 RBU 100.0% UBU 100.0%
 1362165760/3968221184 (34.3%) @4.0x, remaining 8:13 RBU 100.0% UBU 100.0%
 1380646912/3968221184 (34.8%) @4.0x, remaining 8:09 RBU 100.0% UBU 100.0%
 1399128064/3968221184 (35.3%) @4.0x, remaining 8:04 RBU 100.0% UBU 100.0%
 1417609216/3968221184 (35.7%) @4.0x, remaining 8:02 RBU 100.0% UBU 100.0%
 1436057600/3968221184 (36.2%) @4.0x, remaining 7:57 RBU 100.0% UBU 100.0%
 1454538752/3968221184 (36.7%) @4.0x, remaining 7:53 RBU 100.0% UBU 100.0%
 1473019904/3968221184 (37.1%) @4.0x, remaining 7:50 RBU 100.0% UBU 100.0%
 1491501056/3968221184 (37.6%) @4.0x, remaining 7:46 RBU 100.0% UBU 100.0%
 1509982208/3968221184 (38.1%) @4.0x, remaining 7:42 RBU 100.0% UBU 100.0%
 1528463360/3968221184 (38.5%) @4.0x, remaining 7:39 RBU 100.0% UBU 100.0%
 1546911744/3968221184 (39.0%) @4.0x, remaining 7:35 RBU 100.0% UBU 100.0%
 1565392896/3968221184 (39.4%) @4.0x, remaining 7:31 RBU 100.0% UBU 100.0%
 1583874048/3968221184 (39.9%) @4.0x, remaining 7:28 RBU 100.0% UBU 100.0%
 1602355200/3968221184 (40.4%) @4.0x, remaining 7:24 RBU 100.0% UBU 100.0%
 1620836352/3968221184 (40.8%) @4.0x, remaining 7:20 RBU  93.2% UBU 100.0%
 1639317504/3968221184 (41.3%) @4.0x, remaining 7:17 RBU  60.4% UBU 100.0%
 1657765888/3968221184 (41.8%) @4.0x, remaining 7:13 RBU 100.0% UBU 100.0%
 1676247040/3968221184 (42.2%) @4.0x, remaining 7:09 RBU 100.0% UBU 100.0%
 1694728192/3968221184 (42.7%) @4.0x, remaining 7:06 RBU  99.0% UBU 100.0%
 1713209344/3968221184 (43.2%) @4.0x, remaining 7:02 RBU 100.0% UBU 100.0%
 1731690496/3968221184 (43.6%) @4.0x, remaining 6:58 RBU 100.0% UBU 100.0%
 1750171648/3968221184 (44.1%) @4.0x, remaining 6:55 RBU 100.0% UBU 100.0%
 1768652800/3968221184 (44.6%) @4.0x, remaining 6:51 RBU 100.0% UBU 100.0%
 1787101184/3968221184 (45.0%) @4.0x, remaining 6:47 RBU 100.0% UBU 100.0%
 1805582336/3968221184 (45.5%) @4.0x, remaining 6:44 RBU  99.3% UBU 100.0%
 1824063488/3968221184 (46.0%) @4.0x, remaining 6:40 RBU  99.9% UBU 100.0%
 1842544640/3968221184 (46.4%) @4.0x, remaining 6:36 RBU 100.0% UBU 100.0%
 1861025792/3968221184 (46.9%) @4.0x, remaining 6:34 RBU 100.0% UBU 100.0%
 1879506944/3968221184 (47.4%) @4.0x, remaining 6:30 RBU  87.5% UBU 100.0%
 1897988096/3968221184 (47.8%) @4.0x, remaining 6:26 RBU  78.4% UBU 100.0%
 1916469248/3968221184 (48.3%) @4.0x, remaining 6:23 RBU  95.3% UBU 100.0%
 1934917632/3968221184 (48.8%) @4.0x, remaining 6:19 RBU  94.4% UBU 100.0%
 1953398784/3968221184 (49.2%) @4.0x, remaining 6:15 RBU 100.0% UBU 100.0%
 1971879936/3968221184 (49.7%) @4.0x, remaining 6:12 RBU 100.0% UBU 100.0%
 1990361088/3968221184 (50.2%) @4.0x, remaining 6:08 RBU 100.0% UBU 100.0%
 2008842240/3968221184 (50.6%) @4.0x, remaining 6:04 RBU 100.0% UBU 100.0%
 2027323392/3968221184 (51.1%) @4.0x, remaining 6:01 RBU 100.0% UBU 100.0%
 2045804544/3968221184 (51.6%) @4.0x, remaining 5:58 RBU 100.0% UBU 100.0%
 2064285696/3968221184 (52.0%) @4.0x, remaining 5:54 RBU 100.0% UBU 100.0%
 2082734080/3968221184 (52.5%) @4.0x, remaining 5:51 RBU 100.0% UBU 100.0%
 2101215232/3968221184 (53.0%) @4.0x, remaining 5:47 RBU 100.0% UBU 100.0%
 2119696384/3968221184 (53.4%) @4.0x, remaining 5:43 RBU  99.0% UBU 100.0%
 2138177536/3968221184 (53.9%) @4.0x, remaining 5:40 RBU  99.1% UBU 100.0%
 2156658688/3968221184 (54.3%) @4.0x, remaining 5:36 RBU 100.0% UBU 100.0%
 2175139840/3968221184 (54.8%) @4.0x, remaining 5:33 RBU 100.0% UBU 100.0%
 2193620992/3968221184 (55.3%) @4.0x, remaining 5:30 RBU 100.0% UBU 100.0%
 2212102144/3968221184 (55.7%) @4.0x, remaining 5:26 RBU 100.0% UBU 100.0%
 2230583296/3968221184 (56.2%) @4.0x, remaining 5:22 RBU 100.0% UBU 100.0%
 2249064448/3968221184 (56.7%) @4.0x, remaining 5:19 RBU  99.9% UBU 100.0%
 2267512832/3968221184 (57.1%) @4.0x, remaining 5:15 RBU 100.0% UBU 100.0%
 2285993984/3968221184 (57.6%) @4.0x, remaining 5:12 RBU 100.0% UBU 100.0%
 2304475136/3968221184 (58.1%) @4.0x, remaining 5:09 RBU 100.0% UBU 100.0%
 2322956288/3968221184 (58.5%) @4.0x, remaining 5:05 RBU 100.0% UBU 100.0%
 2341437440/3968221184 (59.0%) @4.0x, remaining 5:01 RBU  99.5% UBU 100.0%
 2359918592/3968221184 (59.5%) @4.0x, remaining 4:58 RBU 100.0% UBU 100.0%
 2378399744/3968221184 (59.9%) @4.0x, remaining 4:54 RBU 100.0% UBU 100.0%
 2396880896/3968221184 (60.4%) @4.0x, remaining 4:51 RBU 100.0% UBU 100.0%
 2415362048/3968221184 (60.9%) @4.0x, remaining 4:48 RBU 100.0% UBU 100.0%
 2433843200/3968221184 (61.3%) @4.0x, remaining 4:44 RBU 100.0% UBU 100.0%
 2452324352/3968221184 (61.8%) @4.0x, remaining 4:40 RBU 100.0% UBU 100.0%
 2470805504/3968221184 (62.3%) @4.0x, remaining 4:37 RBU 100.0% UBU 100.0%
 2489253888/3968221184 (62.7%) @4.0x, remaining 4:33 RBU 100.0% UBU 100.0%
 2507735040/3968221184 (63.2%) @4.0x, remaining 4:30 RBU 100.0% UBU 100.0%
 2526216192/3968221184 (63.7%) @4.0x, remaining 4:27 RBU 100.0% UBU 100.0%
 2544697344/3968221184 (64.1%) @4.0x, remaining 4:23 RBU 100.0% UBU 100.0%
 2563178496/3968221184 (64.6%) @4.0x, remaining 4:19 RBU 100.0% UBU 100.0%
 2581659648/3968221184 (65.1%) @4.0x, remaining 4:16 RBU 100.0% UBU 100.0%
 2600140800/3968221184 (65.5%) @4.0x, remaining 4:13 RBU 100.0% UBU 100.0%
 2618621952/3968221184 (66.0%) @4.0x, remaining 4:09 RBU 100.0% UBU 100.0%
 2637103104/3968221184 (66.5%) @4.0x, remaining 4:06 RBU 100.0% UBU 100.0%
 2655584256/3968221184 (66.9%) @4.0x, remaining 4:02 RBU 100.0% UBU 100.0%
 2674065408/3968221184 (67.4%) @4.0x, remaining 3:59 RBU 100.0% UBU 100.0%
 2692546560/3968221184 (67.9%) @4.0x, remaining 3:55 RBU  89.3% UBU 100.0%
 2711027712/3968221184 (68.3%) @4.0x, remaining 3:52 RBU  89.0% UBU 100.0%
 2729508864/3968221184 (68.8%) @4.0x, remaining 3:48 RBU 100.0% UBU 100.0%
 2747957248/3968221184 (69.2%) @4.0x, remaining 3:45 RBU 100.0% UBU 100.0%
 2766438400/3968221184 (69.7%) @4.0x, remaining 3:41 RBU 100.0% UBU 100.0%
 2784919552/3968221184 (70.2%) @4.0x, remaining 3:38 RBU 100.0% UBU 100.0%
 2803400704/3968221184 (70.6%) @4.0x, remaining 3:35 RBU 100.0% UBU 100.0%
 2821881856/3968221184 (71.1%) @4.0x, remaining 3:31 RBU 100.0% UBU 100.0%
 2840363008/3968221184 (71.6%) @4.0x, remaining 3:28 RBU 100.0% UBU 100.0%
 2858844160/3968221184 (72.0%) @4.0x, remaining 3:24 RBU 100.0% UBU 100.0%
 2877325312/3968221184 (72.5%) @4.0x, remaining 3:21 RBU 100.0% UBU 100.0%
 2895806464/3968221184 (73.0%) @4.0x, remaining 3:17 RBU 100.0% UBU 100.0%
 2914287616/3968221184 (73.4%) @4.0x, remaining 3:14 RBU 100.0% UBU 100.0%
 2932768768/3968221184 (73.9%) @4.0x, remaining 3:11 RBU 100.0% UBU 100.0%
 2951249920/3968221184 (74.4%) @4.0x, remaining 3:07 RBU 100.0% UBU 100.0%
 2969731072/3968221184 (74.8%) @4.0x, remaining 3:04 RBU 100.0% UBU 100.0%
 2988212224/3968221184 (75.3%) @4.0x, remaining 3:00 RBU 100.0% UBU 100.0%
 3006693376/3968221184 (75.8%) @4.0x, remaining 2:57 RBU 100.0% UBU 100.0%
 3025174528/3968221184 (76.2%) @4.0x, remaining 2:53 RBU 100.0% UBU 100.0%
 3043655680/3968221184 (76.7%) @4.0x, remaining 2:50 RBU 100.0% UBU 100.0%
 3062136832/3968221184 (77.2%) @4.0x, remaining 2:46 RBU 100.0% UBU 100.0%
 3080617984/3968221184 (77.6%) @4.0x, remaining 2:43 RBU 100.0% UBU 100.0%
 3099099136/3968221184 (78.1%) @4.0x, remaining 2:40 RBU 100.0% UBU 100.0%
 3117580288/3968221184 (78.6%) @4.0x, remaining 2:36 RBU 100.0% UBU 100.0%
 3136028672/3968221184 (79.0%) @4.0x, remaining 2:33 RBU 100.0% UBU 100.0%
 3154509824/3968221184 (79.5%) @4.0x, remaining 2:29 RBU 100.0% UBU 100.0%
 3172990976/3968221184 (80.0%) @4.0x, remaining 2:26 RBU 100.0% UBU 100.0%
 3191472128/3968221184 (80.4%) @4.0x, remaining 2:23 RBU 100.0% UBU 100.0%
 3209953280/3968221184 (80.9%) @4.0x, remaining 2:19 RBU 100.0% UBU 100.0%
 3228434432/3968221184 (81.4%) @4.0x, remaining 2:16 RBU 100.0% UBU 100.0%
 3246915584/3968221184 (81.8%) @4.0x, remaining 2:12 RBU 100.0% UBU 100.0%
 3265396736/3968221184 (82.3%) @4.0x, remaining 2:09 RBU 100.0% UBU 100.0%
 3283877888/3968221184 (82.8%) @4.0x, remaining 2:05 RBU 100.0% UBU 100.0%
 3302359040/3968221184 (83.2%) @4.0x, remaining 2:02 RBU 100.0% UBU 100.0%
 3320840192/3968221184 (83.7%) @4.0x, remaining 1:59 RBU 100.0% UBU 100.0%
 3339321344/3968221184 (84.2%) @4.0x, remaining 1:55 RBU 100.0% UBU 100.0%
 3357802496/3968221184 (84.6%) @4.0x, remaining 1:52 RBU 100.0% UBU 100.0%
 3376283648/3968221184 (85.1%) @4.0x, remaining 1:48 RBU 100.0% UBU 100.0%
 3394764800/3968221184 (85.5%) @4.0x, remaining 1:45 RBU 100.0% UBU 100.0%
 3413245952/3968221184 (86.0%) @4.0x, remaining 1:42 RBU 100.0% UBU 100.0%
 3431727104/3968221184 (86.5%) @4.0x, remaining 1:38 RBU 100.0% UBU 100.0%
 3450208256/3968221184 (86.9%) @4.0x, remaining 1:35 RBU 100.0% UBU 100.0%
 3468689408/3968221184 (87.4%) @4.0x, remaining 1:31 RBU 100.0% UBU 100.0%
 3487170560/3968221184 (87.9%) @4.0x, remaining 1:28 RBU 100.0% UBU 100.0%
 3505651712/3968221184 (88.3%) @4.0x, remaining 1:24 RBU 100.0% UBU 100.0%
 3524132864/3968221184 (88.8%) @4.0x, remaining 1:21 RBU 100.0% UBU 100.0%
 3542614016/3968221184 (89.3%) @4.0x, remaining 1:18 RBU 100.0% UBU 100.0%
 3561095168/3968221184 (89.7%) @4.0x, remaining 1:14 RBU 100.0% UBU 100.0%
 3579576320/3968221184 (90.2%) @4.0x, remaining 1:11 RBU 100.0% UBU 100.0%
 3598057472/3968221184 (90.7%) @4.0x, remaining 1:08 RBU  99.0% UBU 100.0%
 3616538624/3968221184 (91.1%) @4.0x, remaining 1:04 RBU 100.0% UBU 100.0%
 3635019776/3968221184 (91.6%) @4.0x, remaining 1:01 RBU 100.0% UBU 100.0%
 3653500928/3968221184 (92.1%) @4.0x, remaining 0:57 RBU 100.0% UBU 100.0%
 3671982080/3968221184 (92.5%) @4.0x, remaining 0:54 RBU 100.0% UBU 100.0%
 3690463232/3968221184 (93.0%) @4.0x, remaining 0:51 RBU 100.0% UBU 100.0%
 3708944384/3968221184 (93.5%) @4.0x, remaining 0:47 RBU 100.0% UBU 100.0%
 3727425536/3968221184 (93.9%) @4.0x, remaining 0:44 RBU 100.0% UBU 100.0%
 3745906688/3968221184 (94.4%) @4.0x, remaining 0:40 RBU 100.0% UBU 100.0%
 3764387840/3968221184 (94.9%) @4.0x, remaining 0:37 RBU 100.0% UBU  97.1%
 3782868992/3968221184 (95.3%) @4.0x, remaining 0:34 RBU 100.0% UBU 100.0%
 3801350144/3968221184 (95.8%) @4.0x, remaining 0:30 RBU 100.0% UBU 100.0%
 3819831296/3968221184 (96.3%) @4.0x, remaining 0:27 RBU 100.0% UBU 100.0%
 3838312448/3968221184 (96.7%) @4.0x, remaining 0:23 RBU  98.7% UBU 100.0%
 3856793600/3968221184 (97.2%) @4.0x, remaining 0:20 RBU 100.0% UBU 100.0%
 3875274752/3968221184 (97.7%) @4.0x, remaining 0:17 RBU 100.0% UBU 100.0%
 3893755904/3968221184 (98.1%) @4.0x, remaining 0:13 RBU 100.0% UBU 100.0%
 3912237056/3968221184 (98.6%) @4.0x, remaining 0:10 RBU 100.0% UBU 100.0%
 3930718208/3968221184 (99.1%) @4.0x, remaining 0:06 RBU 100.0% UBU 100.0%
 3949199360/3968221184 (99.5%) @4.0x, remaining 0:03 RBU  56.7% UBU 100.0%
 3967680512/3968221184 (100.0%) @4.0x, remaining 0:00 RBU   1.7% UBU 100.0%
/dev/sr0: flushing cache
/dev/sr0: closing track
/dev/sr0: closing session

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1937608 -speed=4 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
1937608
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using ... (some files which names I have deleted for personal reasons)
  0.08% done, estimate finish Sat May 17 10:03:09 2008
  0.10% done, estimate finish Sat May 17 10:03:09 2008
...
 32.02% done, estimate finish Sat May 17 10:15:29 2008
 32.05% done, estimate finish Sat May 17 10:15:28 2008
...
 68.00% done, estimate finish Sat May 17 10:15:15 2008
 68.02% done, estimate finish Sat May 17 10:15:16 2008
...
 99.94% done, estimate finish Sat May 17 10:15:12 2008
 99.97% done, estimate finish Sat May 17 10:15:13 2008
Total translation table size: 0
Total rockridge attributes bytes: 703621
Total directory bytes: 1515896
Path table size(bytes): 5926
Max brk space used 54d000
1937608 extents written (3784 MB)

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid generic_database -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /home/mdutku/tmp/kde-mdutku/k3bSBrFEa.tmp -rational-rock -hide-list /home/mdutku/tmp/kde-mdutku/k3bor9Wba.tmp -joliet -joliet-long -hide-joliet-list /home/mdutku/tmp/kde-mdutku/k3bt3tnIb.tmp -no-cache-inodes -full-iso9660-filenames -disable-deep-relocation -iso-level 2 -path-list /home/mdutku/tmp/kde-mdutku/k3b0tGSWa.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid generic_database -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /home/mdutku/tmp/kde-mdutku/k3bLPmzmc.tmp -rational-rock -hide-list /home/mdutku/tmp/kde-mdutku/k3b1jygMa.tmp -joliet -joliet-long -hide-joliet-list /home/mdutku/tmp/kde-mdutku/k3bzLG44a.tmp -no-cache-inodes -full-iso9660-filenames -disable-deep-relocation -iso-level 2 -path-list /home/mdutku/tmp/kde-mdutku/k3be4pHac.tmp 
```
K3B says it successfully burnt the DVD. /var/log/messages did not show me anything. However I have not been able to read this DVD neither on /media nor /mnt. Mandriva could not mount it automatically, as if it could not read the burned media. dvd+rw-mediainfo however returns me this info
```
[mdutku@localhost ~]$ dvd+rw-mediainfo /dev/sr0
INQUIRY:                [HL-DT-ST][DVDRAM GH20NS10 ][EL00]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Bh, DVD+R
 Current Write Speed:   16.0x1385=22160KB/s
 Write Speed #0:        16.0x1385=22160KB/s
 Write Speed #1:        16.0x1385=22159KB/s
 Write Speed #2:        12.0x1385=16620KB/s
 Write Speed #3:        12.0x1385=16619KB/s
 Write Speed #4:        8.0x1385=11080KB/s
 Write Speed #5:        8.0x1385=11079KB/s
 Write Speed #6:        4.0x1385=5540KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     7.1x1385=9770KB/s@0 -> 16.0x1385=22153KB/s@1961727
                        16.0x1385=22159KB/s@[1961728 -> 2295103]
 Speed Descriptor#0:    02/2295103 R@6.6x1385=9168KB/s W@16.0x1385=22160KB/s
 Speed Descriptor#1:    02/2295103 R@6.6x1385=9168KB/s W@16.0x1385=22159KB/s
 Speed Descriptor#2:    02/2295103 R@6.6x1385=9168KB/s W@12.0x1385=16620KB/s
 Speed Descriptor#3:    02/2295103 R@6.6x1385=9168KB/s W@12.0x1385=16619KB/s
 Speed Descriptor#4:    02/2295103 R@6.6x1385=9168KB/s W@8.0x1385=11080KB/s
 Speed Descriptor#5:    02/2295103 R@6.6x1385=9168KB/s W@8.0x1385=11079KB/s
 Speed Descriptor#6:    02/2295103 R@6.6x1385=9168KB/s W@4.0x1385=5540KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Media ID:              INFOME/R30
 Legacy lead-out at:    2295104*2KB=4700372992
READ DISC INFORMATION:
 Disc status:           appendable
 Number of Sessions:    2
 State of Last Session: empty
 "Next" Track:          2
 Number of Tracks:      2
READ TRACK INFORMATION[#1]:
 Track State:           partial/complete
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            1937616*2KB
READ TRACK INFORMATION[#2]:
 Track State:           blank
 Track Start Address:   1939664*2KB
 Next Writable Address: 1939664*2KB
 Free Blocks:           355440*2KB
 Track Size:            355440*2KB
FABRICATED TOC:
 Track#1  :             14@0
 Track#AA :             14@1937616
 Multi-session Info:    #1@0
READ CAPACITY:          1937616*2048=3968237568
[mdutku@localhost ~]$
```
I will check this DVD further. If I will succeed in reading this media (which I have burned for the first time on a Linux distro), I will update this posting.
**UPDATE:** DVD+R burned by K3B above is corrupt, it cannot be read.

---

### Post by &amp;wP*!) on 2008-05-17
I tried to burn the same media with default settings again, ie. I let K3B to determine the speed, in which case K3B automatically sets the fastest speed. It aborted again.

Hi **AdamWill**, /var/log/messages tells me now this output:
```
May 17 10:47:49 localhost last message repeated 24 times
May 17 10:47:50 localhost kernel: ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
May 17 10:47:50 localhost kernel: ata2.00: cmd a0/01:00:00:00:80/00:00:00:00:00/a0 tag 0 dma 32768 out
May 17 10:47:50 localhost kernel:          cdb 2a 00 00 08 48 f0 00 00  10 00 00 00 00 00 00 00
May 17 10:47:50 localhost kernel:          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
May 17 10:47:50 localhost kernel: ata2.00: status: { DRDY }
May 17 10:47:51 localhost k3b: resmgr: communication failure: No such file or directory
May 17 10:47:53 localhost k3b: resmgr: communication failure: No such file or directory
May 17 10:47:55 localhost kernel: ata2: port is slow to respond, please be patient (Status 0xc0)
May 17 10:47:55 localhost k3b: resmgr: communication failure: No such file or directory
May 17 10:47:59 localhost last message repeated 2 times
May 17 10:48:00 localhost kernel: ata2: soft resetting link
May 17 10:48:00 localhost kernel: ata2.00: configured for UDMA/100
May 17 10:48:00 localhost kernel: ata2: EH complete
May 17 10:48:01 localhost k3b: resmgr: communication failure: No such file or directory
May 17 10:48:33 localhost last message repeated 29 times
```
**dmesg** returns me the same.

The motherboard MSI MS-6590 has the latest BIOS update for its VT8237 chip set with integrated SATA/RAID Controller. On the other side, Windows XP successfully burns this.

I have the suspicion that this has to do with different SATA/IDE channels... What happens on Windows XP is that the burner NERO and the data to be written are on the same harddisk (/dev/hda NTFS). However on Mandriva distro, OS and K3B are on /dev/hdd (EXT3), data to be written is on /dev/hda (NTFS) again. Maybe this combination of 2 hard disks and 1 SATA channel causes this problem.

I will try to burn another media for data which reside on the same hard disk where Mandriva and K3B resides.

---

### Post by &amp;wP*!) on 2008-05-17
No.. Unfortunately writing data which reside on the same hard disk of Mandriva and K3B did not help. K3B aborted again.

Below the /var/log/messages:
```

May 17 11:11:27 localhost kernel: ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
May 17 11:11:27 localhost kernel: ata2.00: cmd a0/01:00:00:00:80/00:00:00:00:00/a0 tag 0 dma 32768 out
May 17 11:11:27 localhost kernel:          cdb 2a 00 00 05 d9 e0 00 00  10 00 00 00 00 00 00 00
May 17 11:11:27 localhost kernel:          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
May 17 11:11:27 localhost kernel: ata2.00: status: { DRDY }
May 17 11:11:29 localhost k3b: resmgr: communication failure: No such file or directory
May 17 11:11:31 localhost k3b: resmgr: communication failure: No such file or directory
May 17 11:11:32 localhost kernel: ata2: port is slow to respond, please be patient (Status 0xc0)
May 17 11:11:33 localhost k3b: resmgr: communication failure: No such file or directory
May 17 11:11:37 localhost last message repeated 2 times
May 17 11:11:37 localhost kernel: ata2: soft resetting link
May 17 11:11:38 localhost kernel: ata2.00: configured for UDMA/100
May 17 11:11:38 localhost kernel: ata2: EH complete
May 17 11:11:39 localhost k3b: resmgr: communication failure: No such file or directory
```
It seems that SATA Controller thinks that DVD Writer is too slow for this setup and raises an exception to CPU. CPU and then the controller resets the DVD Writer...

I think this is either an operating system issue or a K3B issue, because software driver must slow down the data transfer from the IDE harddisk to the SATA channel, on which DVD Writer is mounted. Since it cannot slow down the communication, hardware raises an exception and communication breaks.

I must point out again that none of the distros I have chosen could burn the media in auto mode (Ubuntu, Fedora, OpenSuse and Mandriva). I have used several burner programs. Only Nero on Windows XP could do it automatically. I have burned media only in a slow speed like 4x. 

I think this is either a K3B bug or a Linux Kernel bug. I think this can be a Linux Kernel bug because other distros also fail.

---

### Post by &amp;wP*!) on 2008-05-17
DVD+R burned by K3B with 4x speed cannot be read in Ubuntu and Mandriva. That means K3B on Mandriva could not burn the DVD+R successfully.

I think
```
exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
```
says there is a problem here...

Short summary: None of Linux distro (Ubuntu 8.04, Mandriva 2008 Spring, OpenSuse 10.3, Fedora 8 ) I tried could burn a DVD+R with this hardware, LG GH20NS10 SATA DVD Writer I have bought 1 month ago.

Windows XP can do it with Nero.

I personally believe that this is operating system or K3B problem.

---

### Post by &amp;wP*!) on 2008-05-17
Brasero 0.71 on Ubuntu 8.04 does also have the same problem. I had set up Brasero to write 3x speed :) Even in this slow speed it says timeout :)
```
ubutku@hostubuntu:~$ uname -a
Linux hostubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
ubutku@hostubuntu:~$ dmesg | tail -20
[   80.310130] Bluetooth: RFCOMM ver 1.8
[   81.689512] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   81.689518] tg3: eth0: Flow control is on for TX and on for RX.
[   82.414380] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   82.414397] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   82.414451] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   84.140178] NET: Registered protocol family 17
[   87.065403] NET: Registered protocol family 10
[   87.066124] lo: Disabled Privacy Extensions
[   97.831417] eth0: no IPv6 routers present
[20294.219990] cdrom: This disc doesn't have any tracks I recognize!
[20892.884246] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[20892.884263] ata2.00: cmd a0/01:00:00:00:80/00:00:00:00:00/a0 tag 0 dma 32768 out
[20892.884264]          cdb 2a 00 00 03 0d b0 00 00  10 00 00 00 00 00 00 00
[20892.884266]          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[20892.884269] ata2.00: status: { DRDY }
[20897.920162] ata2: port is slow to respond, please be patient (Status 0xc0)
[20902.900115] ata2: soft resetting link
[20903.391893] ata2.00: configured for UDMA/100
[20903.391929] ata2: EH complete
ubutku@hostubuntu:~$ 

```

---

### Post by AdamWill on 2008-05-18
It definitely seems like some sort of kernel bug. You may have to take this to the hallowed grounds of LKML, unless anyone else reading this forum has a clue. I unfortunately know basically nothing about this kind of low level issue :( Sorry!

---

### Post by &amp;wP*!) on 2008-05-19
> **AdamWill said:**
> It definitely seems like some sort of kernel bug. You may have to take this to the hallowed grounds of LKML, unless anyone else reading this forum has a clue. I unfortunately know basically nothing about this kind of low level issue :( Sorry!

Filed as Linux Kernel Bug #10743:
[http://bugzilla.kernel.org/show_bug.cgi?id=10743](http://bugzilla.kernel.org/show_bug.cgi?id=10743)

Linux Kernel Mailing List has a thread on the problem for this driver.
The problems I stated in this thread might have to do with the problems addressed in that thread:
[http://lkml.org/lkml/2008/2/25/278](http://lkml.org/lkml/2008/2/25/278)

German page about a user who even cannot burn a CD with K3B using this hardware:
[http://www.nabble.com/Probleme-beim-brennen-mit-K3b-td16060165.html](http://www.nabble.com/Probleme-beim-brennen-mit-K3b-td16060165.html)
I also could not burn a CD, either.

Another posting about the issues for this DVD Writer hardware:
[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/95be321e1797ae06](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/95be321e1797ae06)

Another posting about the issues for this DVD Writer hardware:
[http://readlist.com/lists/vger.kernel.org/linux-kernel/92/460293.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/92/460293.html)

All of them address a write issue, not read issue.
All of them address that this DVD Writer is working w/o any problem on Windows operating systems.

---

### Post by AdamWill on 2008-05-21
One thing you can do that upstream would appreciate is to test with a plain upstream kernel. I don't know if there's one in Ubuntu's repositories, but there is in Mandriva's. Install the 'kernel-linus' package and reboot, and select the kernel-linus entry on the boot menu. Some of your hardware might not work with this kernel, don't worry about that. Just try burning a disc and see if it still fails. kernel-linus is a completely vanilla kernel.org kernel with absolutely no Mandriva patches or changes, so if it's broken with that kernel, it's broken upstream :) The version in 2008 Spring is 2.6.25rc6, I believe.

Upstream want you to test 2.6.25.4, I see. That's a bit trickier, it's not in our repo. You may have to build it yourself, or check if Ubuntu has it available somewhere.

---

### Post by terrifickid on 2008-05-26
Hey there,

Running 8.04. I have the same issue. I've used the built in writer, brasero and gnomebaker. All give no errors, but the disc it spits out is useless. WinXp can't read it nor ubuntu. I can burn discs in XP however.

I seem to recall burning discs fine in gutsy, so maybe this is a 8.04 problem?

I have a Toshiba SDR6572M on a sager laptop np5720. 

I've tracked down a number of other folks with the same problem, haven't found a solution though.

I'm a newb, anyone have any answers?

Thanks,
TK

---

### Post by &amp;wP*!) on 2008-05-26
> **terrifickid said:**
> Hey there,

Running 8.04. I have the same issue. I've used the built in writer, brasero and gnomebaker. All give no errors, but the disc it spits out is useless. WinXp can't read it nor ubuntu. I can burn discs in XP however.

I seem to recall burning discs fine in gutsy, so maybe this is a 8.04 problem?

I have a Toshiba SDR6572M on a sager laptop np5720. 

I've tracked down a number of other folks with the same problem, haven't found a solution though.

I'm a newb, anyone have any answers?

Thanks,
TK

Hi terrific boy,

are you sure that you have a SATA DVD Writer? Because LG seems to have also an IDE version for this device.

Please copy-paste the last line of /var/log/messages when you burned a CD/DVD with this device, when using Hardy.

My status is: neither Gutsy nor Hardy can burn any CD or DVD with this device. None of any burning software and none of any Linux distro could burn a disc. However Windows XP can.

According to the error I got in /var/log/messages I think it has to do with the interrupt handling of Linux. A certain combination of hardware interrupts with a specific hardware leads this problem. You probably have such a combination of hardware, that this problem never occurs in Gutsy.

Hardy might have a special interrupt handling mechanism.

In the bug filed at Linu kernel about this device, kernel developer recommended to use a vanilla kernel, which is not easy...

Let's wait and see.

---

### Post by hortimech on 2008-05-29
Hi, mind if I chime in here, I run ubuntu 8.04 on my HP DV9000 series laptop. It did have Kubuntu 7.10 but with several driver problems (mostly sound) it did burn cd's. Now with 8.04, everything I have tried works out of the box, except it will now not burn cd's.
If I boot into windows vista (shudder) it will burn cd's with the same data!

Anybody know what changed between 7.10 and 8.04? or is this a kernel problem?

---

### Post by AdamWill on 2008-05-29
If it's the same bug as this thread's OP has, then yes, it's a kernel problem. Check /var/log/messages and see if you're getting the same messages as the OP.

OP, the kernel upstream wanted you to test - 2.6.25.4 - is now the current version of kernel-linus in 2008 Spring's /contrib/updates repo (it got an update). So you can test it easily now.

---

### Post by &amp;wP*!) on 2008-05-31
> **AdamWill said:**
> If it's the same bug as this thread's OP has, then yes, it's a kernel problem. Check /var/log/messages and see if you're getting the same messages as the OP.

OP, the kernel upstream wanted you to test - 2.6.25.4 - is now the current version of kernel-linus in 2008 Spring's /contrib/updates repo (it got an update). So you can test it easily now.

Sorry for late answer.

After having installed **2.6.25.4-1mdv**, K3B says it wrote DVD successfully but media is corrupt. It cannot be read.

I have installed **kernel-linus-2.6.25.4-1mdv** using Software Managemet program:
```
[root@localhost mdutku]# uname -a
Linux localhost 2.6.25.4-1mdv #1 Sat May 24 16:29:47 EDT 2008 i686 AMD Athlon(tm) XP 2800+ GNU/Linux
[root@localhost mdutku]#
```
To whom it may concern: This package resides in **System->Kernel and Hardware** part in browser field of Software Management. Installing this kernel automatically updated Grub too. I did not need to do anything else.

However media is corrupt. I have used K3B default settings. It did not work. Media info returns me:
```
[root@localhost mdutku]# dvd+rw-mediainfo /dev/sr0
INQUIRY:                [HL-DT-ST][DVDRAM GH20NS10 ][EL00]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Bh, DVD+R
 Current Write Speed:   16.0x1385=22160KB/s
 Write Speed #0:        16.0x1385=22160KB/s
 Write Speed #1:        16.0x1385=22159KB/s
 Write Speed #2:        12.0x1385=16620KB/s
 Write Speed #3:        12.0x1385=16619KB/s
 Write Speed #4:        8.0x1385=11080KB/s
 Write Speed #5:        8.0x1385=11079KB/s
 Write Speed #6:        4.0x1385=5540KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     7.1x1385=9770KB/s@0 -> 16.0x1385=22153KB/s@1961727
                        16.0x1385=22159KB/s@[1961728 -> 2295103]
 Speed Descriptor#0:    02/2295103 R@6.6x1385=9168KB/s W@16.0x1385=22160KB/s
 Speed Descriptor#1:    02/2295103 R@6.6x1385=9168KB/s W@16.0x1385=22159KB/s
 Speed Descriptor#2:    02/2295103 R@6.6x1385=9168KB/s W@12.0x1385=16620KB/s
 Speed Descriptor#3:    02/2295103 R@6.6x1385=9168KB/s W@12.0x1385=16619KB/s
 Speed Descriptor#4:    02/2295103 R@6.6x1385=9168KB/s W@8.0x1385=11080KB/s
 Speed Descriptor#5:    02/2295103 R@6.6x1385=9168KB/s W@8.0x1385=11079KB/s
 Speed Descriptor#6:    02/2295103 R@6.6x1385=9168KB/s W@4.0x1385=5540KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Media ID:              INFOME/R30
 Legacy lead-out at:    2295104*2KB=4700372992
READ DISC INFORMATION:
 Disc status:           appendable
 Number of Sessions:    2
 State of Last Session: empty
 "Next" Track:          2
 Number of Tracks:      2
READ TRACK INFORMATION[#1]:
 Track State:           partial/complete
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            1937616*2KB
READ TRACK INFORMATION[#2]:
 Track State:           blank
 Track Start Address:   1939664*2KB
 Next Writable Address: 1939664*2KB
 Free Blocks:           355440*2KB
 Track Size:            355440*2KB
FABRICATED TOC:
 Track#1  :             14@0
 Track#AA :             14@1937616
 Multi-session Info:    #1@0
READ CAPACITY:          1937616*2048=3968237568
[root@localhost mdutku]#
```
K3B says that it wrote about 6x speed. K3B never aborted or reported anything during burn. I have not seen any error in /var/log/messages, syslog etc.

---

### Post by &amp;wP*!) on 2008-05-31
I have burned another DVD but with no multisession mode. But still the same problem. The burned media are always corrupt, they cannot be read.

No, kernel 2.6.25.4 did not solve my problem.
dmesg returns me
May 31 13:01:45 localhost kernel: cdrom: This disc doesn't have any tracks I recognize!
This message is also in /var/log/kernel/info.log.

I need more diagnostics. /var/log/messages, lspci, lsmod did not give information.

How can I open debug in mkisofs and growisofs in K3B?

---

### Post by &amp;wP*!) on 2008-05-31
K3B is unable to remount the media it burned :)

Nero+Windows XP burns and read the same DVD+R using exactly the same hardware.

---

### Post by &amp;wP*!) on 2008-05-31
Hi Adam,

as you see in my postings above, I have taken 2.6.25.4 vanilla/upstream kernel in Mandriva, the one you have recommended and the upstream recommended in the Kernel Bug page. But even with that I could not burn a DVD. The behaviour is exactly the same I have described in my [[COLOR="DeepSkyBlue"]4th posting[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4978212&postcount=4") in this thread. That means, K3B seems to burn DVD+R media using this hardware and kernel **2.6.25.4**, /var/log/messages etc do not contain any error. However media is corrupt. K3B could not burn the media correctly. Although K3B says it did it successfully, it cannot read/remount the media it burned.

As you see, the behaviour is different between two kernel versions. I am now quite sure that this is definitely Linux kernel bug. Interrupt/exception handling of Linux for this hardware is buggy.

BTW, KDE (when computer is shutdown) and Bluetooth tools on 2.6.25.4 crash with **SIGSEGV** (segmentation fault). That means, this vanilla kernel need to be tested. GDB was not installed.

Please give me a hint, I can test more. I don't get any error from system. I need more diagnostics in K3B front-end or mkisofs etc. I have filed this on Mandriva Expert, KDE also but apart from Linux Kernel Bug page, no other expert has given me a feedback how to come further.

---

### Post by ricardisimo on 2008-06-01
I had difficulty burning onto a dual-layer, but it looks like the problems isn't the DL. Is it the +R that's the problem, or the kernel, or the burning apps? Did the recent kernel update help anything? Thanks.

---

### Post by &amp;wP*!) on 2008-06-01
> **ricardisimo said:**
> I had difficulty burning onto a dual-layer, but it looks like the problems isn't the DL. Is it the +R that's the problem, or the kernel, or the burning apps? Did the recent kernel update help anything? Thanks.
Hi ricardisimo, could you please read the postings carefully? I have already written that I took the recent kernel. This thread is about GH LG20NS10 **SATA** DVD Writer on Mandriva and Ubuntu. This is my case and the problem exists no matter which media I take (CD or DVD, doesn't matter). It's a kind of SATA driver of the Linux kernel problem.

Next time when you post, could you please write, which hardware, which distro you take. There are tons of hardware around. Your hardware might be different, and already has a solution. Check your system and settings again, control everything.

---

### Post by ricardisimo on 2008-06-01
Sorry to pee on your post. Good luck with your problem.

---

### Post by &amp;wP*!) on 2008-06-14
2.6.25.4-1mdv also generates the same hardware exception for SATA device during burning phase:
```
Jun 14 15:12:46 localhost kernel: ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jun 14 15:12:46 localhost kernel: ata2.00: cmd a0/01:00:00:00:80/00:00:00:00:00/a0 tag 0 dma 32768 out
Jun 14 15:12:46 localhost kernel:          cdb 2a 00 00 0c c2 70 00 00  10 00 00 00 00 00 00 00
Jun 14 15:12:46 localhost kernel:          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jun 14 15:12:46 localhost kernel: ata2.00: status: { DRDY }
```Linux kernel bug is still there.

---

### Post by naskopopov on 2008-06-25
Same problem with my SATA DVD Burner Samsung SH-S203D with MB GA-7VT600P-RZ. (VIA VT8237 chipset)
I could't use the DVD burner at all, but is seems the problem is in the default sata_via module. On ubuntu 7.10 this was fixed when i installed via_ubuntu7.10(x86&x86_64)_v-raid_v3.10_driver_appnote_ver0.8 from viaarena.
After this everything worked like a charm, i also noticed speed improvement in other disk operations after installing via_raid module. 
BUT... this won't install with ubuntu 8.04, so i'm without DVD burner on this computer again :)

Hope this helps, somehow.

---

### Post by whizse on 2008-06-30
> **naskopopov said:**
> Same problem with my SATA DVD Burner Samsung SH-S203D with MB GA-7VT600P-RZ. (VIA VT8237 chipset)
I could't use the DVD burner at all, but is seems the problem is in the default sata_via module. On ubuntu 7.10 this was fixed when i installed via_ubuntu7.10(x86&x86_64)_v-raid_v3.10_driver_appnote_ver0.8 from viaarena.


I'm having the same problem with similar hardware.

 Where did you find via drivers for 7.10? All I could find was for 7.04.

---

### Post by whizse on 2008-06-30
Never mind, I [found the driver]("http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=143&Old=1") (it was hidden on a page with old drivers).

Now I can confirm that my hardware actually works and that this really is a bug in sata_via. :)

BTW, there should be no problem for you to install the older kernel and viamraid.ko on 8.04. You will of course need to reboot everytime you need to burn something, but I guess it's better than nothing...

---

### Post by vk2tkw on 2008-06-30
I am experiencing very similar problem. I am new to linux and could not load ubuntu 8.04. Managed to get ver 7.04 running but had similar burner problem. upgraded to 8.04 and problem remained. I am using a HP Presario AMD 64x2, nvidia video card, and Pioneer dvr-109 burner (pata). Initial loading problem was with video but overcame it with older ver and no problem upgrading. Knomebaker refuses to read CD. Brasero seems to read OK but destroys the CD on burning. No problems in Windows XP.

---

### Post by &amp;wP*!) on 2008-07-24
> **naskopopov]Same problem with my SATA DVD Burner Samsung SH-S203D with MB GA-7VT600P-RZ. (VIA VT8237 chipset)[/QUOTE]

[QUOTE=whizse]I'm having the same problem with similar hardware.[/QUOTE]

[QUOTE=vk2tkw said:**
> I am experiencing very similar problem.

You guys do not have the hardware stated in this thread. If you read the thread carefully, you will see that this thread belongs to LG GH20NS10. 

Please, next time when you post, read the postings first. Otherwise it will be very difficult for everyone to get support/help for itself.

---

### Post by sjalex76 on 2008-07-27
> **pencuse said:**
> You guys do not have the hardware stated in this thread. If you read the thread carefully, you will see that this thread belongs to LG GH20NS10. 

Please, next time when you post, read the postings first. Otherwise it will be very difficult for everyone to get support/help for itself.

Are you sure this problem is limited to your hardware? Google "DRDY", and you might find that many people also have similar problems with other SATA devices (hard drives as well as DVD) that cropped up in late kernels and are not present under other OSs. Unless you have some means of ruling out the possibilities of these other issues being the same issue or at least related, it might not be appropriate to be so proprietary about this thread.

---

### Post by thommykane on 2008-07-27
Hello,

i wanted to report a similar bug with Kubuntu 8.04 and K3B
burning with a LG-burner.

Its a pity that it works with Nero or whatsoever in XP.

Here is the output. Since i have already destroyed several empty DVDs,
i tried the simulation and it already gave me an error.
Without simulation no error message appeared, but i cannot read or mount 
the DVD after burning.

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-H62N CL00 (/dev/scd1, ) [CD-R, CD-RW, CD-Rom, DVD-Rom, DVD-R, DVD-RW, DVD-R doppelschichtig, DVD+R, DVD+RW, DVD+R doppelschichtig] [DVD-Rom, DVD-R Sequentiell, Zweischichtige DVD-R Sequentiell, Zweischicht-DVD-R Sprung, DVD-Ram, DVD-RW Eingeschränktes Überbrennen, DVD-RW Sequentiell, DVD+RW, DVD+R, Zweischichtige DVD+R, CD-Rom, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Eingeschränktes Überschreiben, Sprung zwischen DVD-Schichten]

HL-DT-ST DVD-ROM GDRH20N 0L02 (/dev/scd0, ) [CD-Rom, DVD-Rom] [DVD-Rom, DVD+RW, DVD+R, Zweischichtige DVD+R, CD-Rom] [Keine]
Burned media
-----------------------
DVD-R Sequentiell

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd1 obs=32k seek=0'
/dev/scd1: engaging DVD-R DAO upon user request...
/dev/scd1: reserving 2171297 blocks
/dev/scd1: "Current Write Speed" is 4.1x1352KBps.
          0/4446816256 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4446816256 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4446816256 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4446816256 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4446816256 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
    1441792/4446816256 ( 0.0%) @0.3x, remaining 1130:31 RBU 100.0% UBU  94.1%
   19922944/4446816256 ( 0.4%) @4.0x, remaining 96:17 RBU 100.0% UBU 100.0%
   38371328/4446816256 ( 0.9%) @4.0x, remaining 55:31 RBU 100.0% UBU 100.0%
   56852480/4446816256 ( 1.3%) @4.0x, remaining 41:10 RBU 100.0% UBU 100.0%
   75300864/4446816256 ( 1.7%) @4.0x, remaining 34:49 RBU 100.0% UBU 100.0%
   93782016/4446816256 ( 2.1%) @4.0x, remaining 30:10 RBU 100.0% UBU 100.0%
  112230400/4446816256 ( 2.5%) @4.0x, remaining 27:02 RBU 100.0% UBU 100.0%
  130711552/4446816256 ( 2.9%) @4.0x, remaining 25:18 RBU 100.0% UBU 100.0%
  149192704/4446816256 ( 3.4%) @4.0x, remaining 23:31 RBU 100.0% UBU 100.0%
  167641088/4446816256 ( 3.8%) @4.0x, remaining 22:07 RBU 100.0% UBU 100.0%
  186122240/4446816256 ( 4.2%) @4.0x, remaining 21:21 RBU 100.0% UBU 100.0%
  204570624/4446816256 ( 4.6%) @4.0x, remaining 20:23 RBU 100.0% UBU 100.0%
  223051776/4446816256 ( 5.0%) @4.0x, remaining 19:34 RBU 100.0% UBU 100.0%
  241532928/4446816256 ( 5.4%) @4.0x, remaining 19:09 RBU 100.0% UBU 100.0%
  259981312/4446816256 ( 5.8%) @4.0x, remaining 18:31 RBU 100.0% UBU 100.0%
  278462464/4446816256 ( 6.3%) @4.0x, remaining 18:12 RBU 100.0% UBU 100.0%
  296943616/4446816256 ( 6.7%) @4.0x, remaining 17:42 RBU 100.0% UBU 100.0%
  315392000/4446816256 ( 7.1%) @4.0x, remaining 17:14 RBU 100.0% UBU 100.0%
  333873152/4446816256 ( 7.5%) @4.0x, remaining 17:02 RBU 100.0% UBU 100.0%
  352354304/4446816256 ( 7.9%) @4.0x, remaining 16:39 RBU 100.0% UBU 100.0%
  370835456/4446816256 ( 8.3%) @4.0x, remaining 16:18 RBU  99.9% UBU 100.0%
  389283840/4446816256 ( 8.8%) @4.0x, remaining 16:09 RBU 100.0% UBU 100.0%
  407764992/4446816256 ( 9.2%) @4.0x, remaining 15:50 RBU 100.0% UBU 100.0%
  426246144/4446816256 ( 9.6%) @4.0x, remaining 15:33 RBU 100.0% UBU 100.0%
  444727296/4446816256 (10.0%) @4.0x, remaining 15:26 RBU 100.0% UBU 100.0%
  463175680/4446816256 (10.4%) @4.0x, remaining 15:11 RBU 100.0% UBU 100.0%
  481656832/4446816256 (10.8%) @4.0x, remaining 14:57 RBU 100.0% UBU 100.0%
  500137984/4446816256 (11.2%) @4.0x, remaining 14:51 RBU 100.0% UBU 100.0%
  518619136/4446816256 (11.7%) @4.0x, remaining 14:38 RBU 100.0% UBU 100.0%
  537067520/4446816256 (12.1%) @4.0x, remaining 14:26 RBU 100.0% UBU 100.0%
  555548672/4446816256 (12.5%) @4.0x, remaining 14:21 RBU 100.0% UBU 100.0%
  574029824/4446816256 (12.9%) @4.0x, remaining 14:10 RBU 100.0% UBU 100.0%
  592510976/4446816256 (13.3%) @4.0x, remaining 13:59 RBU 100.0% UBU 100.0%
  610992128/4446816256 (13.7%) @4.0x, remaining 13:54 RBU 100.0% UBU 100.0%
  629473280/4446816256 (14.2%) @4.0x, remaining 13:44 RBU 100.0% UBU 100.0%
  647921664/4446816256 (14.6%) @4.0x, remaining 13:34 RBU 100.0% UBU 100.0%
  666402816/4446816256 (15.0%) @4.0x, remaining 13:31 RBU 100.0% UBU 100.0%
  684883968/4446816256 (15.4%) @4.0x, remaining 13:21 RBU 100.0% UBU 100.0%
  703365120/4446816256 (15.8%) @4.0x, remaining 13:13 RBU 100.0% UBU 100.0%
  721846272/4446816256 (16.2%) @4.0x, remaining 13:09 RBU 100.0% UBU 100.0%
  740327424/4446816256 (16.6%) @4.0x, remaining 13:01 RBU 100.0% UBU 100.0%
  758808576/4446816256 (17.1%) @4.0x, remaining 12:52 RBU 100.0% UBU 100.0%
  777289728/4446816256 (17.5%) @4.0x, remaining 12:49 RBU 100.0% UBU 100.0%
  795770880/4446816256 (17.9%) @4.0x, remaining 12:41 RBU 100.0% UBU 100.0%
  814219264/4446816256 (18.3%) @4.0x, remaining 12:33 RBU 100.0% UBU 100.0%
  832700416/4446816256 (18.7%) @4.0x, remaining 12:30 RBU 100.0% UBU 100.0%
  851181568/4446816256 (19.1%) @4.0x, remaining 12:23 RBU 100.0% UBU 100.0%
  869662720/4446816256 (19.6%) @4.0x, remaining 12:16 RBU 100.0% UBU 100.0%
  888143872/4446816256 (20.0%) @4.0x, remaining 12:13 RBU 100.0% UBU 100.0%
  906625024/4446816256 (20.4%) @4.0x, remaining 12:06 RBU 100.0% UBU 100.0%
  925106176/4446816256 (20.8%) @4.0x, remaining 11:59 RBU 100.0% UBU 100.0%
  943587328/4446816256 (21.2%) @4.0x, remaining 11:56 RBU 100.0% UBU 100.0%
  962068480/4446816256 (21.6%) @4.0x, remaining 11:49 RBU 100.0% UBU 100.0%
  980549632/4446816256 (22.1%) @4.0x, remaining 11:43 RBU 100.0% UBU 100.0%
  999030784/4446816256 (22.5%) @4.0x, remaining 11:40 RBU 100.0% UBU 100.0%
 1017511936/4446816256 (22.9%) @4.0x, remaining 11:34 RBU 100.0% UBU 100.0%
 1035993088/4446816256 (23.3%) @4.0x, remaining 11:28 RBU 100.0% UBU 100.0%
 1054474240/4446816256 (23.7%) @4.0x, remaining 11:25 RBU 100.0% UBU 100.0%
 1072955392/4446816256 (24.1%) @4.0x, remaining 11:19 RBU 100.0% UBU 100.0%
 1091436544/4446816256 (24.5%) @4.0x, remaining 11:13 RBU 100.0% UBU 100.0%
 1109917696/4446816256 (25.0%) @4.0x, remaining 11:10 RBU 100.0% UBU 100.0%
 1128398848/4446816256 (25.4%) @4.0x, remaining 11:04 RBU 100.0% UBU 100.0%
 1146880000/4446816256 (25.8%) @4.0x, remaining 10:58 RBU 100.0% UBU 100.0%
 1165361152/4446816256 (26.2%) @4.0x, remaining 10:56 RBU 100.0% UBU 100.0%
 1183842304/4446816256 (26.6%) @4.0x, remaining 10:50 RBU 100.0% UBU 100.0%
 1202323456/4446816256 (27.0%) @4.0x, remaining 10:44 RBU 100.0% UBU 100.0%
 1220804608/4446816256 (27.5%) @4.0x, remaining 10:42 RBU 100.0% UBU 100.0%
 1239285760/4446816256 (27.9%) @4.0x, remaining 10:36 RBU 100.0% UBU 100.0%
 1257766912/4446816256 (28.3%) @4.0x, remaining 10:31 RBU 100.0% UBU 100.0%
 1276248064/4446816256 (28.7%) @4.0x, remaining 10:28 RBU 100.0% UBU 100.0%
 1294729216/4446816256 (29.1%) @4.0x, remaining 10:23 RBU 100.0% UBU 100.0%
 1313210368/4446816256 (29.5%) @4.0x, remaining 10:18 RBU  99.2% UBU 100.0%
 1331691520/4446816256 (29.9%) @4.0x, remaining 10:15 RBU 100.0% UBU 100.0%
 1350205440/4446816256 (30.4%) @4.0x, remaining 10:10 RBU  98.3% UBU 100.0%
 1368686592/4446816256 (30.8%) @4.0x, remaining 10:04 RBU 100.0% UBU 100.0%
 1387167744/4446816256 (31.2%) @4.0x, remaining 10:02 RBU 100.0% UBU 100.0%
 1405648896/4446816256 (31.6%) @4.0x, remaining 9:57 RBU 100.0% UBU 100.0%
 1424130048/4446816256 (32.0%) @4.0x, remaining 9:52 RBU 100.0% UBU 100.0%
 1442611200/4446816256 (32.4%) @4.0x, remaining 9:49 RBU 100.0% UBU 100.0%
 1461092352/4446816256 (32.9%) @4.0x, remaining 9:44 RBU 100.0% UBU 100.0%
 1479573504/4446816256 (33.3%) @4.0x, remaining 9:39 RBU 100.0% UBU 100.0%
 1498054656/4446816256 (33.7%) @4.0x, remaining 9:36 RBU 100.0% UBU 100.0%
 1516535808/4446816256 (34.1%) @4.0x, remaining 9:31 RBU 100.0% UBU 100.0%
 1535049728/4446816256 (34.5%) @4.0x, remaining 9:27 RBU 100.0% UBU 100.0%
 1553530880/4446816256 (34.9%) @4.0x, remaining 9:24 RBU 100.0% UBU 100.0%
 1572012032/4446816256 (35.4%) @4.0x, remaining 9:19 RBU 100.0% UBU 100.0%
 1590493184/4446816256 (35.8%) @4.0x, remaining 9:14 RBU 100.0% UBU 100.0%
 1608974336/4446816256 (36.2%) @4.0x, remaining 9:12 RBU 100.0% UBU 100.0%
 1627455488/4446816256 (36.6%) @4.0x, remaining 9:07 RBU 100.0% UBU 100.0%
 1645936640/4446816256 (37.0%) @4.0x, remaining 9:02 RBU 100.0% UBU 100.0%
 1664417792/4446816256 (37.4%) @4.0x, remaining 8:59 RBU 100.0% UBU 100.0%
 1682931712/4446816256 (37.8%) @4.0x, remaining 8:55 RBU 100.0% UBU 100.0%
 1701412864/4446816256 (38.3%) @4.0x, remaining 8:50 RBU 100.0% UBU 100.0%
 1719894016/4446816256 (38.7%) @4.0x, remaining 8:47 RBU 100.0% UBU 100.0%
 1738375168/4446816256 (39.1%) @4.0x, remaining 8:43 RBU 100.0% UBU 100.0%
 1756856320/4446816256 (39.5%) @4.0x, remaining 8:39 RBU 100.0% UBU 100.0%
 1775337472/4446816256 (39.9%) @4.0x, remaining 8:36 RBU 100.0% UBU 100.0%
 1793818624/4446816256 (40.3%) @4.0x, remaining 8:31 RBU 100.0% UBU 100.0%
 1812332544/4446816256 (40.8%) @4.0x, remaining 8:27 RBU 100.0% UBU 100.0%
 1830813696/4446816256 (41.2%) @4.0x, remaining 8:24 RBU 100.0% UBU 100.0%
 1849294848/4446816256 (41.6%) @4.0x, remaining 8:20 RBU 100.0% UBU 100.0%
 1867776000/4446816256 (42.0%) @4.0x, remaining 8:15 RBU 100.0% UBU 100.0%
 1886257152/4446816256 (42.4%) @4.0x, remaining 8:12 RBU 100.0% UBU 100.0%
 1904771072/4446816256 (42.8%) @4.0x, remaining 8:08 RBU 100.0% UBU 100.0%
 1923252224/4446816256 (43.3%) @4.0x, remaining 8:04 RBU 100.0% UBU 100.0%
 1941733376/4446816256 (43.7%) @4.0x, remaining 8:01 RBU 100.0% UBU 100.0%
 1960214528/4446816256 (44.1%) @4.0x, remaining 7:56 RBU 100.0% UBU 100.0%
 1978695680/4446816256 (44.5%) @4.0x, remaining 7:52 RBU 100.0% UBU 100.0%
 1997176832/4446816256 (44.9%) @4.0x, remaining 7:49 RBU 100.0% UBU 100.0%
 2015690752/4446816256 (45.3%) @4.0x, remaining 7:45 RBU 100.0% UBU 100.0%
 2034171904/4446816256 (45.7%) @4.0x, remaining 7:41 RBU 100.0% UBU 100.0%
 2052653056/4446816256 (46.2%) @4.0x, remaining 7:38 RBU 100.0% UBU 100.0%
 2071134208/4446816256 (46.6%) @4.0x, remaining 7:34 RBU 100.0% UBU 100.0%
 2089615360/4446816256 (47.0%) @4.0x, remaining 7:30 RBU 100.0% UBU 100.0%
 2108129280/4446816256 (47.4%) @4.0x, remaining 7:27 RBU 100.0% UBU 100.0%
 2126610432/4446816256 (47.8%) @4.0x, remaining 7:22 RBU 100.0% UBU 100.0%
 2145091584/4446816256 (48.2%) @4.0x, remaining 7:18 RBU 100.0% UBU 100.0%
 2163572736/4446816256 (48.7%) @4.0x, remaining 7:15 RBU 100.0% UBU 100.0%
 2182053888/4446816256 (49.1%) @4.0x, remaining 7:11 RBU 100.0% UBU 100.0%
 2200567808/4446816256 (49.5%) @4.0x, remaining 7:07 RBU 100.0% UBU 100.0%
 2219048960/4446816256 (49.9%) @4.0x, remaining 7:04 RBU 100.0% UBU 100.0%
 2237530112/4446816256 (50.3%) @4.0x, remaining 7:00 RBU 100.0% UBU 100.0%
 2256011264/4446816256 (50.7%) @4.0x, remaining 6:56 RBU 100.0% UBU 100.0%
 2274525184/4446816256 (51.1%) @4.0x, remaining 6:53 RBU 100.0% UBU 100.0%
 2293006336/4446816256 (51.6%) @4.0x, remaining 6:49 RBU 100.0% UBU 100.0%
 2311487488/4446816256 (52.0%) @4.0x, remaining 6:45 RBU 100.0% UBU 100.0%
 2329968640/4446816256 (52.4%) @4.0x, remaining 6:42 RBU 100.0% UBU 100.0%
 2348449792/4446816256 (52.8%) @4.0x, remaining 6:38 RBU 100.0% UBU 100.0%
 2366963712/4446816256 (53.2%) @4.0x, remaining 6:34 RBU 100.0% UBU 100.0%
 2385444864/4446816256 (53.6%) @4.0x, remaining 6:31 RBU 100.0% UBU 100.0%
 2403926016/4446816256 (54.1%) @4.0x, remaining 6:27 RBU 100.0% UBU 100.0%
 2422407168/4446816256 (54.5%) @4.0x, remaining 6:23 RBU 100.0% UBU 100.0%
 2440921088/4446816256 (54.9%) @4.0x, remaining 6:20 RBU 100.0% UBU 100.0%
 2459435008/4446816256 (55.3%) @4.0x, remaining 6:16 RBU 100.0% UBU 100.0%
 2477883392/4446816256 (55.7%) @4.0x, remaining 6:12 RBU 100.0% UBU 100.0%
 2496364544/4446816256 (56.1%) @4.0x, remaining 6:09 RBU 100.0% UBU 100.0%
 2514878464/4446816256 (56.6%) @4.0x, remaining 6:05 RBU 100.0% UBU 100.0%
 2533359616/4446816256 (57.0%) @4.0x, remaining 6:01 RBU 100.0% UBU 100.0%
 2551840768/4446816256 (57.4%) @4.0x, remaining 5:58 RBU 100.0% UBU 100.0%
 2570354688/4446816256 (57.8%) @4.0x, remaining 5:54 RBU 100.0% UBU 100.0%
 2588835840/4446816256 (58.2%) @4.0x, remaining 5:51 RBU 100.0% UBU 100.0%
 2607316992/4446816256 (58.6%) @4.0x, remaining 5:47 RBU 100.0% UBU 100.0%
 2625798144/4446816256 (59.0%) @4.0x, remaining 5:43 RBU 100.0% UBU  94.1%
 2644312064/4446816256 (59.5%) @4.0x, remaining 5:40 RBU 100.0% UBU 100.0%
 2662793216/4446816256 (59.9%) @4.0x, remaining 5:37 RBU 100.0% UBU 100.0%
 2681274368/4446816256 (60.3%) @4.0x, remaining 5:33 RBU 100.0% UBU 100.0%
 2699788288/4446816256 (60.7%) @4.0x, remaining 5:30 RBU 100.0% UBU 100.0%
 2718269440/4446816256 (61.1%) @4.0x, remaining 5:26 RBU 100.0% UBU 100.0%
 2736750592/4446816256 (61.5%) @4.0x, remaining 5:22 RBU 100.0% UBU 100.0%
 2755231744/4446816256 (62.0%) @4.0x, remaining 5:19 RBU 100.0% UBU 100.0%
 2773745664/4446816256 (62.4%) @4.0x, remaining 5:15 RBU 100.0% UBU 100.0%
 2792226816/4446816256 (62.8%) @4.0x, remaining 5:11 RBU 100.0% UBU 100.0%
 2810707968/4446816256 (63.2%) @4.0x, remaining 5:08 RBU 100.0% UBU 100.0%
 2829189120/4446816256 (63.6%) @4.0x, remaining 5:04 RBU 100.0% UBU 100.0%
 2847703040/4446816256 (64.0%) @4.0x, remaining 5:00 RBU 100.0% UBU 100.0%
 2866184192/4446816256 (64.5%) @4.0x, remaining 4:57 RBU 100.0% UBU 100.0%
 2884665344/4446816256 (64.9%) @4.0x, remaining 4:54 RBU  99.8% UBU 100.0%
 2903179264/4446816256 (65.3%) @4.0x, remaining 4:50 RBU 100.0% UBU 100.0%
 2921660416/4446816256 (65.7%) @4.0x, remaining 4:47 RBU 100.0% UBU 100.0%
 2940141568/4446816256 (66.1%) @4.0x, remaining 4:43 RBU 100.0% UBU 100.0%
 2958655488/4446816256 (66.5%) @4.0x, remaining 4:39 RBU 100.0% UBU 100.0%
 2977136640/4446816256 (66.9%) @4.0x, remaining 4:36 RBU 100.0% UBU 100.0%
 2995617792/4446816256 (67.4%) @4.0x, remaining 4:32 RBU 100.0% UBU 100.0%
 3014131712/4446816256 (67.8%) @4.0x, remaining 4:29 RBU 100.0% UBU 100.0%
 3032612864/4446816256 (68.2%) @4.0x, remaining 4:25 RBU 100.0% UBU 100.0%
 3051094016/4446816256 (68.6%) @4.0x, remaining 4:22 RBU 100.0% UBU 100.0%
 3069607936/4446816256 (69.0%) @4.0x, remaining 4:18 RBU 100.0% UBU 100.0%
 3088089088/4446816256 (69.4%) @4.0x, remaining 4:15 RBU 100.0% UBU 100.0%
 3106570240/4446816256 (69.9%) @4.0x, remaining 4:11 RBU 100.0% UBU 100.0%
 3125084160/4446816256 (70.3%) @4.0x, remaining 4:07 RBU 100.0% UBU 100.0%
 3143565312/4446816256 (70.7%) @4.0x, remaining 4:04 RBU 100.0% UBU 100.0%
 3162046464/4446816256 (71.1%) @4.0x, remaining 4:00 RBU 100.0% UBU 100.0%
 3180527616/4446816256 (71.5%) @4.0x, remaining 3:57 RBU 100.0% UBU 100.0%
 3199041536/4446816256 (71.9%) @4.0x, remaining 3:54 RBU 100.0% UBU 100.0%
 3217522688/4446816256 (72.4%) @4.0x, remaining 3:50 RBU 100.0% UBU 100.0%
 3236003840/4446816256 (72.8%) @4.0x, remaining 3:46 RBU 100.0% UBU 100.0%
 3254517760/4446816256 (73.2%) @4.0x, remaining 3:43 RBU 100.0% UBU 100.0%
 3272998912/4446816256 (73.6%) @4.0x, remaining 3:39 RBU 100.0% UBU 100.0%
 3291480064/4446816256 (74.0%) @4.0x, remaining 3:36 RBU 100.0% UBU 100.0%
 3309993984/4446816256 (74.4%) @4.0x, remaining 3:32 RBU 100.0% UBU 100.0%
 3328475136/4446816256 (74.9%) @4.0x, remaining 3:29 RBU 100.0% UBU 100.0%
 3346989056/4446816256 (75.3%) @4.0x, remaining 3:25 RBU 100.0% UBU 100.0%
 3365470208/4446816256 (75.7%) @4.0x, remaining 3:22 RBU 100.0% UBU 100.0%
 3383951360/4446816256 (76.1%) @4.0x, remaining 3:18 RBU 100.0% UBU 100.0%
 3402432512/4446816256 (76.5%) @4.0x, remaining 3:15 RBU 100.0% UBU 100.0%
 3420946432/4446816256 (76.9%) @4.0x, remaining 3:11 RBU 100.0% UBU 100.0%
 3439427584/4446816256 (77.3%) @4.0x, remaining 3:08 RBU 100.0% UBU 100.0%
 3457941504/4446816256 (77.8%) @4.0x, remaining 3:04 RBU 100.0% UBU 100.0%
 3476422656/4446816256 (78.2%) @4.0x, remaining 3:01 RBU 100.0% UBU 100.0%
 3494903808/4446816256 (78.6%) @4.0x, remaining 2:57 RBU 100.0% UBU 100.0%
 3513417728/4446816256 (79.0%) @4.0x, remaining 2:54 RBU 100.0% UBU 100.0%
 3531898880/4446816256 (79.4%) @4.0x, remaining 2:50 RBU 100.0% UBU 100.0%
 3550380032/4446816256 (79.8%) @4.0x, remaining 2:47 RBU 100.0% UBU 100.0%
 3568893952/4446816256 (80.3%) @4.0x, remaining 2:43 RBU 100.0% UBU 100.0%
 3587375104/4446816256 (80.7%) @4.0x, remaining 2:40 RBU 100.0% UBU 100.0%
 3605856256/4446816256 (81.1%) @4.0x, remaining 2:36 RBU 100.0% UBU 100.0%
 3624370176/4446816256 (81.5%) @4.0x, remaining 2:33 RBU 100.0% UBU 100.0%
 3642884096/4446816256 (81.9%) @4.0x, remaining 2:30 RBU 100.0% UBU 100.0%
 3661332480/4446816256 (82.3%) @4.0x, remaining 2:26 RBU 100.0% UBU 100.0%
 3679846400/4446816256 (82.8%) @4.0x, remaining 2:22 RBU 100.0% UBU 100.0%
 3698327552/4446816256 (83.2%) @4.0x, remaining 2:19 RBU 100.0% UBU 100.0%
 3716841472/4446816256 (83.6%) @4.0x, remaining 2:16 RBU 100.0% UBU 100.0%
 3735322624/4446816256 (84.0%) @4.0x, remaining 2:12 RBU 100.0% UBU 100.0%
 3753803776/4446816256 (84.4%) @4.0x, remaining 2:09 RBU 100.0% UBU 100.0%
 3772317696/4446816256 (84.8%) @4.0x, remaining 2:05 RBU 100.0% UBU 100.0%
 3790798848/4446816256 (85.2%) @4.0x, remaining 2:02 RBU 100.0% UBU 100.0%
 3809280000/4446816256 (85.7%) @4.0x, remaining 1:58 RBU 100.0% UBU 100.0%
 3827793920/4446816256 (86.1%) @4.0x, remaining 1:55 RBU 100.0% UBU 100.0%
 3846275072/4446816256 (86.5%) @4.0x, remaining 1:51 RBU 100.0% UBU 100.0%
 3864788992/4446816256 (86.9%) @4.0x, remaining 1:48 RBU 100.0% UBU 100.0%
 3883270144/4446816256 (87.3%) @4.0x, remaining 1:44 RBU 100.0% UBU 100.0%
 3901751296/4446816256 (87.7%) @4.0x, remaining 1:41 RBU 100.0% UBU 100.0%
 3920265216/4446816256 (88.2%) @4.0x, remaining 1:38 RBU 100.0% UBU 100.0%
 3938746368/4446816256 (88.6%) @4.0x, remaining 1:34 RBU 100.0% UBU 100.0%
 3957260288/4446816256 (89.0%) @4.0x, remaining 1:31 RBU 100.0% UBU 100.0%
 3975741440/4446816256 (89.4%) @4.0x, remaining 1:27 RBU 100.0% UBU 100.0%
 3994222592/4446816256 (89.8%) @4.0x, remaining 1:24 RBU 100.0% UBU 100.0%
 4012736512/4446816256 (90.2%) @4.0x, remaining 1:20 RBU 100.0% UBU 100.0%
 4031217664/4446816256 (90.7%) @4.0x, remaining 1:17 RBU 100.0% UBU 100.0%
 4049698816/4446816256 (91.1%) @4.0x, remaining 1:13 RBU 100.0% UBU 100.0%
 4068212736/4446816256 (91.5%) @4.0x, remaining 1:10 RBU 100.0% UBU 100.0%
 4086726656/4446816256 (91.9%) @4.0x, remaining 1:06 RBU 100.0% UBU 100.0%
 4105207808/4446816256 (92.3%) @4.0x, remaining 1:03 RBU 100.0% UBU 100.0%
 4123688960/4446816256 (92.7%) @4.0x, remaining 1:00 RBU 100.0% UBU 100.0%
 4142170112/4446816256 (93.1%) @4.0x, remaining 0:56 RBU 100.0% UBU 100.0%
 4160684032/4446816256 (93.6%) @4.0x, remaining 0:53 RBU 100.0% UBU 100.0%
 4179165184/4446816256 (94.0%) @4.0x, remaining 0:49 RBU 100.0% UBU 100.0%
 4197679104/4446816256 (94.4%) @4.0x, remaining 0:46 RBU 100.0% UBU 100.0%
 4216160256/4446816256 (94.8%) @4.0x, remaining 0:42 RBU 100.0% UBU 100.0%
 4234641408/4446816256 (95.2%) @4.0x, remaining 0:39 RBU 100.0% UBU 100.0%
 4253155328/4446816256 (95.6%) @4.0x, remaining 0:35 RBU 100.0% UBU 100.0%
 4271669248/4446816256 (96.1%) @4.0x, remaining 0:32 RBU 100.0% UBU 100.0%
 4290150400/4446816256 (96.5%) @4.0x, remaining 0:29 RBU 100.0% UBU 100.0%
 4308631552/4446816256 (96.9%) @4.0x, remaining 0:25 RBU 100.0% UBU 100.0%
 4327112704/4446816256 (97.3%) @4.0x, remaining 0:22 RBU 100.0% UBU 100.0%
 4345626624/4446816256 (97.7%) @4.0x, remaining 0:18 RBU 100.0% UBU 100.0%
 4364107776/4446816256 (98.1%) @4.0x, remaining 0:15 RBU 100.0% UBU 100.0%
 4382621696/4446816256 (98.6%) @4.0x, remaining 0:11 RBU 100.0% UBU 100.0%
 4401102848/4446816256 (99.0%) @4.0x, remaining 0:08 RBU 100.0% UBU 100.0%
 4419584000/4446816256 (99.4%) @4.0x, remaining 0:05 RBU  81.2% UBU 100.0%
 4438097920/4446816256 (99.8%) @4.0x, remaining 0:01 RBU  26.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @1.9x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
 4446814208/4446816256 (100.0%) @0.0x, remaining 0:00 RBU   0.1% UBU 100.0%
:-[ WRITE@LBA=2121a0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( write failed: Input/output error
/dev/scd1: flushing cache
:-( unable to FLUSH CACHE: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd1=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2171297 -use-the-force-luke=dummy -use-the-force-luke=dao:2171297 -dvd-compat -speed=2.4 -overburn -use-the-force-luke=bufsize:32m 


many greetings,

Thommy  :-|

---

### Post by miciurin on 2008-07-29
i do not think that this k3b bug is related to a specific hardware but to a software bug. I have the exact same problem: k3B either quits with the generic "write error" or produces a corrupt disc. This is in kubuntu 8.04 and happends with a NEC ide burner and also with a LiteOn SATA burner. 

I have installed in wine a programm called IMGBURN and it works without any problems (at least there is no need to switch operating systems just to burn a CD).

---

### Post by &amp;wP*!) on 2008-07-30
> **sjalex76 said:**
> Are you sure this problem is limited to your hardware? Google "DRDY", and you might find that many people also have similar problems with other SATA devices (hard drives as well as DVD) that cropped up in late kernels and are not present under other OSs. Unless you have some means of ruling out the possibilities of these other issues being the same issue or at least related, it might not be appropriate to be so proprietary about this thread.
Hi sjalex, there are several hardware products which produce the same error. If several different products produce the same error, does not mean they have the same problem. The cause can be one of the 1000 different things. Exception handling is a wide topic in Linux operating system for the complexity of hardware these days.

The Linux kernel developer confirmed my sentence above in the Linux Kernel Bug I have opened for this hardware:
[http://bugzilla.kernel.org/show_bug.cgi?id=10743](http://bugzilla.kernel.org/show_bug.cgi?id=10743)

I am **Utku** who opened the Linux kernel bug page. If you look at our discussion there, linux kernel driver for VT6420 does not support correctly this hardware. This is specific for this product. The developer suggested that each different hardware product must have its own bug page.

Similary we must handle different threads in Ubuntu Forums or anywhere else on internet, so that we keep the information on internet cleanly to remedy information pollution. Redundant and disorganized information is the biggest issue in Linux threads. If you look at Ubuntu forum postings in other discussions you will get what I mean. This is a handicap for open software, makes difficult/time consuming to access correct information and to inform hardware vendor, because hardware developers also use our information to improve Linux support of hardware products.

Therefore I suggest all forum members not to use this thread for the bugs/issues seen in hardware products other than GH20NS10.

---

### Post by &amp;wP*!) on 2008-07-30
> **miciurin said:**
> i do not think that this k3b bug is related to a specific hardware but to a software bug.

In the Kernel Bug page below the Linux kernel developer thinks that it is related to the kernel:
[http://bugzilla.kernel.org/show_bug.cgi?id=10743](http://bugzilla.kernel.org/show_bug.cgi?id=10743)
This is not a K3B bug. This is a Linux kernel bug.

> I have the exact same problem: k3B either quits with the generic "write error" or produces a corrupt disc. This is in kubuntu 8.04 and happends with a NEC ide burner and also with a LiteOn SATA burner.

This thread addresses SATA protocol problems, so your IDE burner is out of question.

LiteOn SATA burner can have different hardware, which is not supported by Linux kernel and might be different than GH20NS10, the only hardware discussed in this thread.

> I have installed in wine a programm called IMGBURN and it works without any problems (at least there is no need to switch operating systems just to burn a CD).

Combination of Wine and Linux might not show a kernel bug, because Wine might be using Windows resources to burn hardware.

Therefore your setups are not relevant in this thread discussion.

---

### Post by thommykane on 2008-07-30
> **pencuse said:**
> 
**Utku**: Therefore I suggest all forum members not to use this thread for the bugs/issues seen in hardware products other than GH20NS10.

Don't you think, that it would be better to concentrate not on one certain hardware model, but instead on perhaps a product line of one certain company, like LG. Since probably they use similar chip sets and firmware in their product lines ? 
I have LG GSA-H62N SATA DVD WRITER and suffer from this problem as well, as written before.

---

### Post by &amp;wP*!) on 2008-07-30
> **thommykane said:**
> Don't you think, that it would be better to concentrate not on one certain hardware model, but instead on perhaps a product line of one certain company, like LG. Since probably they use similar chip sets and firmware in their product lines ? 
I have LG GSA-H62N SATA DVD WRITER and suffer from this problem as well, as written before.
Hi Thommykane, basically you are right to say that all LG products can be covered in this thread. However I have 3 points to object to this:

[LIST=1]
[*]Kernel developer also did not recommend to use the same [Kernel bug]("http://bugzilla.kernel.org/show_bug.cgi?id=10743") of LG GH20NS10 for your hardware (GSA-H62). For more information, see the discussion in the bug thread.
[*]The Linux bug for GH20NS10 DVD Writer is not trivial. I am discussing with the developer for 1,5 months, and has been tested in a wide range of combinations and setups of distributions and applcations. It is being discussed in a wide spectrum of aspects and therefore when addressing other hardware, it will be very difficult to identify the issues for GH20NS10.
[*]A company might not use the same electronics in different products for a certain application. That means, my GH20NS10 and your GSA-H62N might have different hardware. Companies like LG give very little information about the internal electronics of their products (as it can be seen in the datasheets below) but kernel developer also confirms that the problems seen in your hardware are different than the ones in my hardware.
[/LIST]

Here are the datasheets of these DVD Writers from the same company:
[GH20NS10 datasheet]("http://www.lgcommercial.com/downloads/pdf/19445_GH20NS10_010308.pdf") 
[GSA-H62N datasheet]("http://us.lge.com/download/product/file/1000003672/h_gsah62n_spec_sheet.pdf")

Response times, buffer capacity etc. the same but I still insist that the electronics might be different.

Therefore I propose to separate the topics of different hardware and not to use one for several, even if they belong to the same vendor.

---

### Post by &amp;wP*!) on 2008-08-01
Kernel developer mentioned in the Linux kernel bug report that the next patch which fixes the problem of the SATA DVD Writer GH20NS10 will be implemented in 2.6.28.

Until then, no workaround is available.

---

### Post by gcshum on 2009-01-05
Has anyone tried the LG GH20NS10 SATA DVD writer to see if it works with the new 2.6.28 kernel?

---

### Post by &amp;wP*!) on 2009-01-11
> **gcshum said:**
> Has anyone tried the LG GH20NS10 SATA DVD writer to see if it works with the new 2.6.28 kernel?

I doubt it does. According to the discussions between exercisers and the OS developer in the Kernel Bug page stated that even 2.6.28 did not solve the problem.

Intrepid Ibex has now 2.6.27-xx. The fastest way to test 2.6.28 is to take a rolling-release distro like Arch Linux but Arch Linux is time-consuming to set up. I have one but out-dated. I need time to test it, which I do not have at the moment.

Stay tuned.

---

### Post by gcshum on 2009-02-03
It is very strange. My friend installed Ibex and this drive works fine for him. I believe Ibex uses 2.24.27 kernel. I'm still on Hardy. But since Jackalope is coming soon. I'll wait for it.

---

