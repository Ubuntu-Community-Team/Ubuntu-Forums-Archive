---
title: "Wireless USB Problems - Been trying for days! Ralink 2070 Chipset/Ubuntu 9.04/i686."
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by SonOfEctheow on 2010-03-11
Sorry in advance... I know you all get a lot of questions regarding wireless usb adapters, but I am at the end of my rope! The adapter I purchased (Zonet ZEW2508 ) uses the Ralink 2070 chipset - a fact that originally excited me because Ralink seems to be fairly loving to the Linux community. However, despite my best efforts I can't get the thing to work. Initially I tried following directions to set up the driver you can download from the Ralink website. The directions I found were written February first, and Ralink updated the driver February eighth - so as far as I can tell the directions no longer work. After screwing around trying to figure that out for a while I decided to give ndiswrapper a go. Initially this seemed promising. I just harvested the drivers from the CD and followed one of the many ndiswrapper directions available - most helpful seemed initially to be the Ndiswrapper Troubleshooting Guide found in this forum, however the solutions offered there didn't work either. When I throw an *ndiswrapper -l* into the terminal it looks promising at first, it tells me the driver is installed and the device is present, but it just doesn't work. When I try *iwconfig, *or *iwlist scan* it tells me "no wireless extensions," and "interface doesn't support scanning" respectively. The only devices even listed are lo, eth0, and pan0. There's no wlan0 or anything of the sort. Any ideas would be appreciated. I'm fairly new to linux and have been struggling with getting my wireless to work - I'm on my second card (the first was a Linksys WUSB100 v.2), and my third week. I'm using 9.04. Thanks.

---

### Post by chili555 on 2010-03-11
With the device inserted, please post:```
lsmod | grep -e rt2 -e ndis
```Thanks.

---

