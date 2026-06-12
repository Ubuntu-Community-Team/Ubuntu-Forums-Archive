---
title: "buggy network manager in oneiric"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2012-02-09
I have a problem where after getting connected to internet with a little browsing activity I notice that my internet suddenly disappears.The NetworkManager  asks me for authorisation every few minutes, suggesting that it was losing the connection or something similar. Initially thought it to be a driver issue so purged the broadcom STA driver and installed b43 firmware.But the problem did not go. So re installed the broadcom STA driver.

my specs

```
Ubuntu 11.10
 3.0.0-12-generic x86_64
 lspci -nnk | grep -iA2 net
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: wl

```Some times after a reboot I can connect and some times I can not connect.If connected to a wireless network after few minutes the a window pops up asking to enter authorization again.Upon entering it does not connects and this pop up comes 3-4 times.Then finally the device becomes unusable.I have to finally reboot it.

---

