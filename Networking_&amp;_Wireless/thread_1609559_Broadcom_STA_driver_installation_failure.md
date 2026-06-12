---
title: "Broadcom STA driver installation failure"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by anairda on 2010-10-30
Hello everyone, 

My wireless card (ID: 14e4:4328  Broadcom Corporation BCM4328 802.11a/b/g/n) doesn't work on ubuntu 10.04 (lucid). 

When i try to install the recommended proprietary driver I'm told that the installation fail and that I sould check the log file:

**2010-10-30 19:25:55,952** DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
**2010-10-30 19:27:32,433 **DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
**2010-10-30 19:28:09,391** DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
**2010-10-30 19:28:14,570** WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

**2010-10-30 19:28:14,571** WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
**2010-10-30 19:28:14,611** DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

and sure enough the folder /sys/module/wl/drivers does not exist. (not even the folder /sys/module/wl/ )

What does this mean? 

PS: If I should post more information about my system, it would be great if you could tell me how to find it. I'm quite new to Linux.

---

