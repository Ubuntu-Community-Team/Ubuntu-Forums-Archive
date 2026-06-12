---
title: "No Internet/WiFi in Ubuntu 9.10"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by BicycleFiend on 2011-10-18
Hi all,

I'm running Ubuntu 9.10 dual-booted with Windows 7, and my Ubuntu partition won't detect any wireless networks and won't connect via ethernet either, as far as I can tell. I have an Intel Centrino Advanced-N 6230 wireless card, and I've tried looking for the relevant Linux drivers for the card online, but I've had no luck. Can anyone point me in the right direction or help me figure out what the problem might be?

Thanks!

---

### Post by chili555 on 2011-10-19
I believe the needed driver is installed but possibly not the required firmware. Let's do some troubleshooting. Please open a terminal and run and post:```
lspci -nn | grep 0280
dmesg | grep iwl
```Thanks.

---

