---
title: "b43 packet injection"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by EvilRobotDrew on 2008-12-10
i am attempting to get packet injection to work on my Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). i am trying to follow this tutorial [http://aircrack-ng.org/doku.php?id=b43](http://aircrack-ng.org/doku.php?id=b43) but get the following error when trying to patch my kernel:

root@drew-laptop:/usr/src/linux-headers-2.6.24-21# ls
arch                          Documentation  init    lib       samples   usr
b43-injection-2.6.24-4.patch  drivers        ipc     Makefile  scripts
block                         fs             Kbuild  mm        security
crypto                        include        kernel  net       sound

root@drew-laptop:/usr/src/linux-headers-2.6.24-21# patch -p1 -i b43-injection-2.6.24-4.patch

can't find file to patch at input line 7
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|# Kernel >= 2.6.24.1 highly recommended
|#  Fixes injection speed (up to 350 pps)
|#  Fixes fragmented injection (requires mac80211 patch too)
|diff -bBur linux-2.6.24.4/drivers/net/wireless/b43/main.c linux-2.6.24.4-sud/drivers/net/wireless/b43/main.c
|--- linux-2.6.24.4/drivers/net/wireless/b43/main.c	2008-04-05 16:25:11.000000000 +0200
|+++ linux-2.6.24.4-sud/drivers/net/wireless/b43/main.c	2008-04-05 16:45:11.000000000 +0200
--------------------------
File to patch: ^C             
root@drew-laptop:/usr/src/linux-headers-2.6.24-21# 

I have absolutely no idea what i am doing, please help!

---

