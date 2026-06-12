---
title: "Wireless Broke After System Update [Broadcom 4313]"
date: 2012-11-08
forum: Networking &amp; Wireless
---

### Post by ajukilibodin on 2012-11-08
EDIT: This fixed my problem. 
    sudo apt-get install linux-headers-generic     sudo apt-get install --reinstall bcmwl-kernel-source     sudo modprobe wl 




After a fresh Gnome Shell Remix 12.10 installation, my wireless worked perfect. Then I did the software update, and well, it's gone.

lspci -nn | grep 02[80]0 | grep "Broadcom Corporation"
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)


 iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

---

### Post by capawi on 2012-11-27
Cheers for the fix, worked perfectly :KS

---

### Post by jchanam on 2013-01-21
Thank you so much!
It worked perfectly!!!

I've been searching for one hour to get the fix but doesn't find it until I see your post!

---

