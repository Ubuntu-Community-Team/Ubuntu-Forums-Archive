---
title: "Poor radio performance Intel 3945ABG"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by kakotako on 2009-12-24
I just replaced the Broadcom card that came with my Dell Mini 9 for Intel 3945ABG. On the upside the Intel card connects to my AP instantly after a fresh boot which is much better than what the Mini 9 stock wifi card can do.

Something is affecting the receiver radio sensitivity. I am sitting 5 meters from my AP. The Broadcom card routinely got -50 dBm while the Intel is getting -61 dBm.

iwlist wlan0 scan returns 2 or 3 cells at best whereas the Broadcom was picking up 5-6 neighbors' networks. If I execute iwlist wlan0 scan repeatedly the card finds some of these other networks but never lists them all together as if it is channel hopping at slow speed.

This is evident in Kismet, the card will find nearly all neighboring APs but due to low sensitivity it's not receiving the beacons constantly.

I am pretty sure I plugged in the antennas well. The connectors snapped in and are pretty snug. I bought the card used. It has Intel logos on it but I read somewhere about fake Intel cards.

I am wondering if this is a hardware issue with the card or something software related. I wasn't able to prevent the original Dell/Broadcom wl module from loading. I disabled it under System/Administration/Hardware Drivers and also created a /etc/modprobe.d/blacklist-custom file with wl line in it. Could there be some conflict between the wl and iwl3945 going on?

Here is lsmod | grep iwl
```
iwl3945                89204  0 
iwlwifi_mac80211      213988  1 iwl3945
cfg80211               14984  1 iwlwifi_mac802
```11

and dmesg | grep iwl
```
[   18.344028] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   18.344038] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   18.344314] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   18.459400] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   18.463676] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
```


I am just starting out in Linux so be gentle please. I am using Hardy that came preinstalled on Mini 9.

---

