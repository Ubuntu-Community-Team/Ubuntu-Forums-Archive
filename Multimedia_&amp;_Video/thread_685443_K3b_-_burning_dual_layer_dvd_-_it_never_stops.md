---
title: "K3b - burning dual layer dvd - it never stops"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by tr333 on 2008-02-02
I'm having problems trying to copy a dual-layer dvd in k3b (Ubuntu 7.10).  I set the options to save the disc first as a iso image in /tmp, and I also reduced the speed from 8x to 4x to prevent buffer problems.  After the "overall progress" bar got to 100%, the "writing data" bar was stuck on 98% and the "buffer status" was hovering around 95-100%.  The amount of data written to the dvd seemed to be climbing way above the limit given for the disc.  How can I fix this to copy a dual-layer dvd properly?

K3b lastlog.log. It was up to 1200% before i cancelled it, so I cut it down to post here.:
> [System] K3b Version: 1.0.3
[System] KDE Version: 3.5.8
[System] QT Version:  3.3.7
[System] Kernel:      2.6.22-14-generic
[Devices] TSSTcorp DVD+-RW TS-L632H D300 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]
[K3bDataTrackReader] reading sectors 0 to 3933695 with sector size 2048. Length: 3933696 sectors, 8056209408 bytes.
[K3bDataTrackReader] using buffer size of 64 blocks.
[K3bDataTrackReader] Read a total of 3933696 sectors (8056209408 bytes)
[Used versions] growisofs: 7.0.1
[Burned media] DVD+R Dual Layer
[growisofs command:] /usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=break:1966848 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m 
[growisofs] Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
[growisofs] :-? Failed to change write speed: 2770->3324
[growisofs] /dev/scd0: splitting layers at 1966848 blocks
[growisofs] /dev/scd0: "Current Write Speed" is 2.5x1352KBps.
[growisofs]     9142272/421294080 ( 2.2%) @2.0x, remaining 3:45 RBU 100.0% UBU  76.7%
[growisofs]    20283392/421294080 ( 4.8%) @2.4x, remaining 2:38 RBU 100.0% UBU  99.9%
[growisofs]    31424512/421294080 ( 7.5%) @2.4x, remaining 2:16 RBU 100.0% UBU  99.9%
[growisofs]    40697856/421294080 ( 9.7%) @2.0x, remaining 2:20 RBU 100.0% UBU  99.6%
[growisofs]    51806208/421294080 (12.3%) @2.4x, remaining 2:08 RBU 100.0% UBU  99.9%
[growisofs]    62947328/421294080 (14.9%) @2.4x, remaining 1:59 RBU 100.0% UBU  99.9%
[growisofs]    72744960/421294080 (17.3%) @2.1x, remaining 1:59 RBU 100.0% UBU  99.9%
[growisofs]    83886080/421294080 (19.9%) @2.4x, remaining 1:52 RBU 100.0% UBU  99.9%
[growisofs]    95027200/421294080 (22.6%) @2.4x, remaining 1:46 RBU 100.0% UBU  99.3%
[growisofs]   106168320/421294080 (25.2%) @2.4x, remaining 1:43 RBU 100.0% UBU  99.4%
[growisofs]   117473280/421294080 (27.9%) @2.4x, remaining 1:38 RBU 100.0% UBU  95.9%
[growisofs]   128581632/421294080 (30.5%) @2.4x, remaining 1:33 RBU 100.0% UBU  99.9%
[growisofs]   139722752/421294080 (33.2%) @2.4x, remaining 1:30 RBU 100.0% UBU  99.7%
[growisofs]   150863872/421294080 (35.8%) @2.4x, remaining 1:26 RBU 100.0% UBU  99.9%
[growisofs]   162004992/421294080 (38.5%) @2.4x, remaining 1:21 RBU 100.0% UBU  98.5%
[growisofs]   173113344/421294080 (41.1%) @2.4x, remaining 1:18 RBU 100.0% UBU  99.9%
[growisofs]   184254464/421294080 (43.7%) @2.4x, remaining 1:14 RBU 100.0% UBU  99.9%
[growisofs]   195395584/421294080 (46.4%) @2.4x, remaining 1:10 RBU 100.0% UBU  96.1%
[growisofs]   206536704/421294080 (49.0%) @2.4x, remaining 1:07 RBU 100.0% UBU  99.9%
[growisofs]   217677824/421294080 (51.7%) @2.4x, remaining 1:03 RBU  99.9% UBU  86.5%
[growisofs]   228818944/421294080 (54.3%) @2.4x, remaining 0:59 RBU 100.0% UBU  97.2%
[growisofs]   239927296/421294080 (57.0%) @2.4x, remaining 0:56 RBU 100.0% UBU  99.9%
[growisofs]   251133952/421294080 (59.6%) @2.4x, remaining 0:52 RBU 100.0% UBU  99.9%
[growisofs]   262242304/421294080 (62.2%) @2.4x, remaining 0:49 RBU 100.0% UBU  99.7%
[growisofs]   273383424/421294080 (64.9%) @2.4x, remaining 0:45 RBU 100.0% UBU  99.9%
[growisofs]   284524544/421294080 (67.5%) @2.4x, remaining 0:42 RBU 100.0% UBU  99.9%
[growisofs]   295665664/421294080 (70.2%) @2.4x, remaining 0:38 RBU 100.0% UBU  98.8%
[growisofs]   306806784/421294080 (72.8%) @2.4x, remaining 0:35 RBU 100.0% UBU  99.9%
[growisofs]   317947904/421294080 (75.5%) @2.4x, remaining 0:31 RBU 100.0% UBU  99.9%
[growisofs]   329089024/421294080 (78.1%) @2.4x, remaining 0:28 RBU 100.0% UBU  99.9%
[growisofs]   338821120/421294080 (80.4%) @2.1x, remaining 0:25 RBU 100.0% UBU  99.6%
[growisofs]   349962240/421294080 (83.1%) @2.4x, remaining 0:22 RBU 100.0% UBU  99.7%
[growisofs]   361103360/421294080 (85.7%) @2.4x, remaining 0:18 RBU 100.0% UBU  99.4%
[growisofs]   372211712/421294080 (88.3%) @2.4x, remaining 0:15 RBU 100.0% UBU  99.9%
[growisofs]   383352832/421294080 (91.0%) @2.4x, remaining 0:11 RBU 100.0% UBU  99.9%
[growisofs]   394493952/421294080 (93.6%) @2.4x, remaining 0:08 RBU 100.0% UBU  99.9%
[growisofs]   405667840/421294080 (96.3%) @2.4x, remaining 0:04 RBU 100.0% UBU  93.8%
[growisofs]   416776192/421294080 (98.9%) @2.4x, remaining 0:01 RBU 100.0% UBU  96.5%
[growisofs]   427917312/421294080 (101.6%) @2.4x, remaining 0:-2 RBU 100.0% UBU  99.9%
[growisofs]   437682176/421294080 (103.9%) @2.1x, remaining 0:-5 RBU 100.0% UBU  99.9%
[growisofs]   448299008/421294080 (106.4%) @2.3x, remaining 0:-8 RBU 100.0% UBU  99.9%
[growisofs]   459440128/421294080 (109.1%) @2.4x, remaining 0:-11 RBU 100.0% UBU  99.9%
[growisofs]   470581248/421294080 (111.7%) @2.4x, remaining 0:-15 RBU 100.0% UBU  99.9%
[growisofs]   481722368/421294080 (114.3%) @2.4x, remaining 0:-18 RBU 100.0% UBU  99.9%
[growisofs]   492830720/421294080 (117.0%) @2.4x, remaining 0:-21 RBU 100.0% UBU  99.9%
[growisofs]   503971840/421294080 (119.6%) @2.4x, remaining 0:-25 RBU 100.0% UBU  99.6%
[growisofs]   515112960/421294080 (122.3%) @2.4x, remaining 0:-28 RBU 100.0% UBU  99.6%
[growisofs]   526254080/421294080 (124.9%) @2.4x, remaining 0:-32 RBU 100.0% UBU  99.4%
[growisofs]   537395200/421294080 (127.6%) @2.4x, remaining 0:-35 RBU 100.0% UBU  99.9%
[growisofs]   548536320/421294080 (130.2%) @2.4x, remaining 0:-38 RBU 100.0% UBU  98.5%
[growisofs]   559677440/421294080 (132.8%) @2.4x, remaining 0:-42 RBU 100.0% UBU  99.9%
[growisofs]   570818560/421294080 (135.5%) @2.4x, remaining 0:-45 RBU 100.0% UBU  97.7%
[growisofs]   581926912/421294080 (138.1%) @2.4x, remaining 0:-49 RBU 100.0% UBU  99.9%
[growisofs]   593068032/421294080 (140.8%) @2.4x, remaining 0:-52 RBU 100.0% UBU  99.3%
[growisofs]   604209152/421294080 (143.4%) @2.4x, remaining 0:-56 RBU 100.0% UBU  99.9%
[growisofs]   613941248/421294080 (145.7%) @2.1x, remaining 0:-58 RBU 100.0% UBU  99.9%
[growisofs]   625082368/421294080 (148.4%) @2.4x, remaining -1:-2 RBU 100.0% UBU 100.0%
[growisofs]   636223488/421294080 (151.0%) @2.4x, remaining -1:-5 RBU 100.0% UBU  99.9%
[growisofs]   647331840/421294080 (153.7%) @2.4x, remaining -1:-9 RBU 100.0% UBU  98.5%
[growisofs]   658472960/421294080 (156.3%) @2.4x, remaining -1:-12 RBU 100.0% UBU  97.2%
[growisofs]   669745152/421294080 (159.0%) @2.4x, remaining -1:-16 RBU 100.0% UBU  94.0%
[growisofs]   680886272/421294080 (161.6%) @2.4x, remaining -1:-19 RBU 100.0% UBU  99.6%
[growisofs]   691994624/421294080 (164.3%) @2.4x, remaining -1:-22 RBU 100.0% UBU  99.9%
[growisofs]   703168512/421294080 (166.9%) @2.4x, remaining -1:-26 RBU 100.0% UBU  99.9%
[growisofs]   714309632/421294080 (169.6%) @2.4x, remaining -1:-29 RBU 100.0% UBU  94.9%
[growisofs]   725352448/421294080 (172.2%) @2.4x, remaining -1:-33 RBU 100.0% UBU  99.9%
[growisofs]   736591872/421294080 (174.8%) @2.4x, remaining -1:-36 RBU 100.0% UBU  99.9%
[growisofs]   747732992/421294080 (177.5%) @2.4x, remaining -1:-39 RBU 100.0% UBU  99.9%
[growisofs]   758874112/421294080 (180.1%) @2.4x, remaining -1:-43 RBU 100.0% UBU  99.9%
[growisofs]   770048000/421294080 (182.8%) @2.4x, remaining -1:-46 RBU 100.0% UBU  91.7%
[growisofs]   781221888/421294080 (185.4%) @2.4x, remaining -1:-49 RBU 100.0% UBU  99.9%
[growisofs]   792395776/421294080 (188.1%) @2.4x, remaining -1:-53 RBU 100.0% UBU  99.6%
[growisofs]   803536896/421294080 (190.7%) @2.4x, remaining -1:-56 RBU 100.0% UBU  99.9%
[growisofs]   814710784/421294080 (193.4%) @2.4x, remaining -1:-59 RBU 100.0% UBU  99.7%
[growisofs] /dev/scd0: flushing cache

---

### Post by carlinuxlearner on 2008-02-05
When burning a Dual layer DVD you need to set the size to 8.5GB, there should be some button or check box to do this. I use GnomeBaker, and you just select what size the DVD is then tell it to burn.

---

### Post by gsmanners on 2008-02-05
K3b has bugs related to any files over 4GB. I'm not sure you can burn anything but small files to a dual layer with it.

---

### Post by tr333 on 2008-02-06
It seems like Brasero is also having problems when trying to copy a dual-layer dvd.
I managed to do it by using the burning capabilities of the Nautilus file manager - right click on the dvd icon on the desktop and click "copy".  It didn't ask me for any options other than to insert the blank cd when required.

---

