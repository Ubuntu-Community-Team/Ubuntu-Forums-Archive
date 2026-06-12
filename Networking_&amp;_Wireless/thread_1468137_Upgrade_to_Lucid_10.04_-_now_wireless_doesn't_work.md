---
title: "Upgrade to Lucid 10.04 - now wireless doesn't work - Dell laptop (inspiron 1525)"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by winterstein on 2010-05-01
I've just upgraded my laptop to 10.04. 
My wireless is no longer working. The network widget says "Wireless Networks: device not ready"

The laptop is a 32bit Dell Inspiron 1525. 
I think the wireless card may be a "Broadcom Corporation BCM4312 802.11b/g (rev 01)" - this is the most plausible line from lpsci.

I've tried all the commands listed at [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)
Most of them either fail to run, or output nothing relevant (e.g. I use | grep w and get nothing).
Running "sudo lshw -C network" returned amongst other stuff:

 *-network DISABLED
description: Wireless interface
logical name: wlan0
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Please help, using short words & assume I know nothing!

---

### Post by /Michael/ on 2010-05-01
Try to install the proprietary Broadcom STA wireless driver (/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb on the installation media). I'm running a Lenovo S10 which has also a Broadcom wireless card.

You have to reboot after the installation to load the kernel module.

---

### Post by pdc on 2010-05-01
hello winterstein

here is a guide for the broadcom on ubuntu

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

they indeed would suggest the Broadcom STA wireless driver

and the thread above gives you detailed instructions

---

### Post by bgvianyc on 2010-05-01
I just upgraded as well and my while my wireless card does work, it takes much longer for it to connect to the wireless router and the connect to WEP dialogue box pops up several times before it finally connects instead of just connecting on its own.

---

