---
title: "Toshiba Laptop Wireless -- no connection"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by DaveM59 on 2010-11-05
Currently running 64 bit Ubuntu 10.4 dual-boot on my Toshiba Satellite T235D.  For two months everything worked fine, then a few days ago, the laptop would no longer connect to my wireless network.  Network details: hidden network, no security.  Network manager could see the network but would not connect.  Ethernet connection worked fine.  Booted into Windows and wireless connection works, so hardware is not the problem.  I did some searching and found many recommendations to replace Network Manager with WICD so I did that -- installed WICD from the Ubuntu repository and completely removed Network Manager.  That seemed to do the trick, but it lasted only until I rebooted.  Now WICD is doing the same thing Network Manager did.  It shows the network (as x00/x00/x00etc.) but does not connect. If I set the router to broadcast the SSID the laptop connects, but as soon as I reset it to "do not broadcast" it disconnects, and attempts to connect return a "failed to obtain IP address" error message.

Any advice on troubleshooting this problem would be appreciated.

---

