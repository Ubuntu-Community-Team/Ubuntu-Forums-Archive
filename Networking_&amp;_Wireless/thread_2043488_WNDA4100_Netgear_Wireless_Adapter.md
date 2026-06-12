---
title: "WNDA4100 Netgear Wireless Adapter"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by d0wngrade on 2012-08-16
Hello ubuntuforums, this is my first post here and I'm just trying to get some help with my adapter working.
I've read around a lot and got ndiswrapper installed, and I even found my driver (.INF) file for my adapter and got it installed via ndiswrapper. If I run a "ndiswrapper -l" it shows the driver is installed and the device is present...But I still don't have any wireless extensions in iwconfig, wlan0 isn't even initialized. So if anyone has any tips or anything, please let me know. Thank you!!

~d0wngrade

---

### Post by chili555 on 2012-08-17
Are there any clues here?```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Thanks.

---

