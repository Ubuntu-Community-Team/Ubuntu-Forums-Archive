---
title: "Wireless problems with D-Link wua-1340"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by zdub10 on 2010-03-20
Hello all, 

I have been struggling with this for some time and have not been able to make it work. I just installed Karmic and am trying to connect to my wireless network using my D-Link wua-1340 wireless adapter. 
I have installed ndiswrapper and the dr71wu.inf driver. However, when I do ```
ndiswrapper -l
``` I get ```
dr71wu : driver installed 
device (07D1 : 3C04) present (alternate driver: rt73usb
```
This is confusing to me because I added the rt73usb driver to the blacklist. Also, when I do ```
iwconfig
``` I get no mention of wlan0. 

Any advice? Thanks a lot.

---

