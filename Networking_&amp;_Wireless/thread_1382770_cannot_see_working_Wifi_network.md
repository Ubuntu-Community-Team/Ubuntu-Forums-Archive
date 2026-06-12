---
title: "cannot see working Wifi network"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by ga2re2t on 2010-01-16
Hello all, this is my first post on this forum.

In brief, my situation and problem:
 - Running Ubuntu 9.04
 - Ubuntu+Wifi had worked with my previous router
 - Wifi is not detecting a new router (whether in WEP or WPA mode), but detects several neighbours' routers
 - My wifi enabled mobile phone can detect and connect to my WPA enabled router.
 - My new router is 802.11n enabled, but I would have assumed backwards compatibility with my 802.11b/g wifi card?

What I've tried:
 - rebooting router and PC
 - changing security modes: WEP, WPA-TKIP, WPA-AES
 - changing router SSID
 - hiding then un-hiding router SSID
 - connecting manually by using "Connect to hidden network". This initially worked, but no longer does!
 - changed the default wifi channel of my router (from 11 to 6)

I think that's about it. My router is supplied by my internet provider ("Free" in France). A neighbour has the same one, which my Ubuntu can detect. Maybe there's some form of conflict? I'm really stumped.
Any help would be greatly appreciated.

Thanks,
GA2RE2T

---

### Post by Nazareth_patrice on 2010-01-16
what is your wifi interface ?

---

### Post by bkratz on 2010-01-16
> **ga2re2t said:**
> Hello all, this is my first post on this forum.

In brief, my situation and problem:
 - Running Ubuntu 9.04
 - Ubuntu+Wifi had worked with my previous router
 - Wifi is not detecting a new router (whether in WEP or WPA mode), but detects several neighbours' routers
 - My wifi enabled mobile phone can detect and connect to my WPA enabled router.
 - My new router is 802.11n enabled, but I would have assumed backwards compatibility with my 802.11b/g wifi card?

What I've tried:
 - rebooting router and PC
 - changing security modes: WEP, WPA-TKIP, WPA-AES
 - changing router SSID
 - hiding then un-hiding router SSID
 - connecting manually by using "Connect to hidden network". This initially worked, but no longer does!
 - changed the default wifi channel of my router (from 11 to 6)

I think that's about it. My router is supplied by my internet provider ("Free" in France). A neighbour has the same one, which my Ubuntu can detect. Maybe there's some form of conflict? I'm really stumped.
Any help would be greatly appreciated.

Thanks,
GA2RE2T

Have you tried dropping to the terminal and typing in

sudo iwlist scan

also to find out what wireless card you have
lspci | grep Wireless
(that is LSPCI in lowercase)

and finally you might copy/paste the results of:

sudo lshw -C network
(LSHW in lowercase)
back here

---

### Post by ga2re2t on 2010-01-16
Thanks for picking up my problem.

network still not visible with iwlist scan
(and I'm sure it's broadcasting cos my mobile phone can connect to it)

from lspci, my card is:
00:07.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

From lshw, here is the relevant info:
*-network:1
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: wmaster0
       version: 00
       serial: 00:08:a1:a9:70:a6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg

---

### Post by ga2re2t on 2010-01-16
It seems like I found what the problem was:
My router is suppose to automatically choose the most appropriate wifi channel (from 1 to 14)
However, it was choosing a wifi channel that was being used elsewhere in our appartment block, so using:
```
sudo iwlist scan | grep "Channel"
```I was able to see what channel's were being occupied. (Thanks bkratz for the info)
 I then configured my router manually to channel 7.

This seems to have done the trick.

---

### Post by bkratz on 2010-01-16
Congratulations, sorry I missed your last posting, but glad you solved it!

---

