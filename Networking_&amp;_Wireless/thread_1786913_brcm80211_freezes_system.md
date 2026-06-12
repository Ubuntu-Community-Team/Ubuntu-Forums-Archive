---
title: "brcm80211 freezes system"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by poorchava on 2011-06-20
Hardware: Acer Aspire One 722, AMD Ontario C50, 4 GB DDR3, Broadcom 4313 wifi card
Software: Win 7 + Ubuntu 11.04 (linux booted from separate boot partition, not mbr if that matters)

I've recently installed the above Ubuntu distro. The wireless worked at first, but with proprietary STA driver installed. I wanted to try using aircrack-ng so i figured that i need a proper wifi card driver. 

As b43 seems not to support my chipset i wanted to compile the module from sources as written in [http://ubuntuforums.org/showthread.php?t=1617380&highlight=brcm80211](http://ubuntuforums.org/showthread.php?t=1617380&highlight=brcm80211).

I've downloaded git repositories but I've failed to make the brcm8011 because of missing kernel header files (which - oddly enough - were in their proper place, just weren't detected by Makefile script or something). Anyway when idea with compilation failed i read some more stuff and it turned out that brcm80211 was already included in kernel 2.6.38 which I have. Searching in files proved that brcm80211.ko module is already there, just not running in kernel.

Question 1: Why doesn Ubuntu want to install proprietary driver while it has open driver available?

So i've removed the proprietary driver and did 
```
sudo modprobe mac80211 sudo insmod brcm80211.ko
```


Now whenever i boot Ubuntu the system freezes while loading GNOME. I figured that something is wrong with wireless driver and is freezes my system (needs hard reset) while trying to connect.

Question 2: How do i turn that stuff off, so that i could boot normally? How to force GNOME not try to use wireless? I can only boot into recovery mode.

---

