---
title: "Lenovo G580 networking problems"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by p0ntiac on 2013-01-16
I have similar problems as users with BCM4313 wlan, and Artheos LAN drivers. At installing ubuntu I had wifi, but no lan. Searching in forums I found a solition that made my lan work. But same time the wifi has gone. I also updated the kernel to 3.5.0-21.

Following command makes my wifi work:

```
apt-get remove linux-backports-modules-*
```Following command makes my lan work:

```
apt-get install linux-backports-cw-3.6-quantal-generic
```I need a solution (I think lot of us) where both the lan and wifi work at the same time.

thanks

EDIT: running ..cw-3.6-3.5.0-21 I had both wifi and lan at the same time, but after restart remained only the lan.

---

### Post by chili555 on 2013-01-17
I'm not at all sure a solution to the conflict is even possible, however, I enjoy a challenge and I'm willing to give it a shot. I assume the drivers in question are wl for wireless and alx for ethernet; please confirm. 

I believe the problem is that the backports package builds many drivers, including wireless, when all you need is alx. The handling of mac80211, cfg80211, lib80211 and whomever80211 is very different from the method used in bcmwl-kernel-source. Therefor, when backports installs its methodology, it installs methods incompatible with wl and wl no longer works! What we need is a driver package for alx *ONLY* that doesn't install lots of xx80211 modules. I may have just that! Before we proceed, let's get some hardware details:```
lspci -nn | grep -e 0200 -e 0280
arch
uname -r
```I am optimistic.

---

