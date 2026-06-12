---
title: "No wifi on Dell Mini after installing Ubuntu 12.10"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by sole75 on 2012-11-18
Hi, just installed Ubuntu 12.10 on Dell Inspiron Mini 1012. No wifi, so run these at terminal (connected to internet via ethernet):

07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

sudo modprobe wl
FATAL: Module wl not found

sudo apt-get install bcmwl-kernel-source
E: Unable to locate package bcmwl-kernel-source

sudo apt-get install firmware-b43-lpphy-installer
E: Unable to locate package firmware-b43-lpphy-installer


Does anyone have an idea what to do in order to get wifi?
Thanks for responds in advance!

---

### Post by Hadaka on 2012-11-18
Hi, this should work for you.

[http://ubuntuforums.org/showthread.php?t=2080753&highlight=bcmwl&page=3](http://ubuntuforums.org/showthread.php?t=2080753&highlight=bcmwl&page=3)

---

### Post by gnusci on 2012-11-18
> **sole75 said:**
> Hi, just installed Ubuntu 12.10 on Dell Inspiron Mini 1012. No wifi, so run these at terminal (connected to internet via ethernet):

07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

sudo modprobe wl
FATAL: Module wl not found

sudo apt-get install bcmwl-kernel-source
E: Unable to locate package bcmwl-kernel-source

sudo apt-get install firmware-b43-lpphy-installer
E: Unable to locate package firmware-b43-lpphy-installer


Does anyone have an idea what to do in order to get wifi?
Thanks for responds in advance!

Why don't you give a look to this post and give more details so you can get help

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by serpico007 on 2013-04-04
I upgraded to 12.10 recently from 12.04 and everything worked fine including wifi. Was your install fresh 12.10?

---

