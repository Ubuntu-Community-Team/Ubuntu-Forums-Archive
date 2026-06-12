---
title: "Ralink RT2870STA Wireless driver compilation issues"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by shanept on 2011-11-22
Hi,

I am having trouble compiling my wireless driver for my Edimax EW-7718Un wireless USB modem.

My errors are here: [http://pastebin.com/ZSRAksK9](http://pastebin.com/ZSRAksK9)
I am following this: [http://ubuntuforums.org/showthread.php?p=6600309](http://ubuntuforums.org/showthread.php?p=6600309)

Stuck at 6.
I can copy RT2870STA.dat however the rt2870sta.ko file is not created.

Following the advice of this tutorial: [http://www.matthartley.com/rt2870-linux-driver-on-ubuntu-10-04/](http://www.matthartley.com/rt2870-linux-driver-on-ubuntu-10-04/)
I tried make then make install however that also told me the file did not exist.

This is all double dutch to me! 

Any help would be greatly appreciated.

Thanks,
Shane T

---

### Post by pdc on 2011-11-22
I believe this driver has been in the linux kernel since 2.6.29

eg 

[https://wiki.archlinux.org/index.php/Rt2870](https://wiki.archlinux.org/index.php/Rt2870)

and 

[http://wiki.debian.org/rt2870sta](http://wiki.debian.org/rt2870sta)

if you type in the command

> lsmod if you copy and paste back what you get

this thread

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

suggests data you could post to the forum to seek more help

---

### Post by shanept on 2011-11-22
> **pdc said:**
> I believe this driver has been in the linux kernel since 2.6.29
pdc, My device does connect and after less than 30 seconds disconnects again. I know this is to do with ubuntu as it works fine on Debian (after a kernel upgrade and installing firmware-ralink), and in ubuntu 11.10 it works fine, its in 10.10 it doesnt work. I switched back as I hate unity :P

Bus 001 Device 008: ID 7392:7718 Edimax Technology Co., Ltd EW-7718UN 802.11n Wireless Adapter [Ralink RT2870]

---

### Post by shanept on 2011-11-22
Never mind, this seems to have done it.

Thanks for your help!

[http://ubuntuforums.org/archive/index.php/t-1671799.htmlhttp://ubuntuforums.org/archive/index.php/t-1671799.html](http://ubuntuforums.org/archive/index.php/t-1671799.htmlhttp://ubuntuforums.org/archive/index.php/t-1671799.html)

---

### Post by xcal8bur on 2011-11-22
I'm having the same issue as shanept with my RT2870 chipset based adapter. But that link in that post that shanept put up does not work anymore. Can someone tell me where I can find the modified drivers for this chipset.

---

### Post by xcal8bur on 2011-11-22
Nevermind guys I found the full version link. Thanks anyway.

---

