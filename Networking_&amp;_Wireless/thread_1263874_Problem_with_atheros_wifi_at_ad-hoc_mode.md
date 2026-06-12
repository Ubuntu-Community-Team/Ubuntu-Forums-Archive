---
title: "Problem with atheros wifi at ad-hoc mode"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by cawook on 2009-09-11
I have just tried livecd distribution of ubuntu 9.04 and how I was surprised, when I discovered that I can finally set my atheros wireless card to ad-hoc mode.

ifconfig wlan0 down
iwconfig wlan0 mode ad-hoc
ifconfig wlan0 up
working!

So I install ubuntu on hdd, but when I boot from it, ad-hoc mode is not working again, just like previous releases of ubuntu. When I type iwconfig wlan0 mode ad-hoc, result is "Operation not supported".

System loaded same driver (ath5k) as at livecd session, but probably something is different.

What am I doing wrong?

---

### Post by cawook on 2009-09-21
Halo, nobody know?

---

