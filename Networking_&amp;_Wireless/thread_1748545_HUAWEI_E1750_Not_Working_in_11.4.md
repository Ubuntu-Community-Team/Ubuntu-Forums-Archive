---
title: "HUAWEI E1750 Not Working in 11.4"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by Eyebee on 2011-05-03
I have upgraded my Acer Aspire One from 10.10 to 11.4. 

My T-Mobile UK Broadband Dongle worked fine until then, and now it won't work. 

It starts flashing green (as it did before) and then it flashes blue.

I can see a Mobile Broadband option in Network Manager (including the settings that worked in 10.10). However, a right click on the network icon in the top panel does NOT give me any corresponding (T-Mobile) connect option, nor is there anywhere in there with a check against Mobile Broadband as there was in 10.10

---

### Post by alexfish on 2011-05-05
not sure of the relevance of the right click , and not seen

can post results of these commands from the terminal
```
nm-tool
```
```
usb-devices
```find the lines relevant to the device and post only those lines.
also have you tried deleting the connection, then  remake the connection

alexfish

---

