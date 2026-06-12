---
title: "get-iplayer works on cable but not wireless connection"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by ajgreeny on 2013-06-24
I am now running xubuntu 12.04 on my netbook, and though the web connection works fine either wireless or on cable connection, I can never download any BBC TV programmes when on wireless, but all works fine when on a cable connection.  I can always get the full tv or radio cache lists updated on wireless, just not actually download anything.

This problem was the same on Ubuntu 10.04 and also Lubuntu 11.10, so has been a long term problem for me.

The netbook has an atheros adapter
```
description:     Wireless interface
product:     AR9285 Wireless Network Adapter (PCI-Express)
vendor:     Atheros Communications Inc.
physical id:     
0
bus info:     
pci@0000:02:00.0
logical name:     
wlan0
version:     01
serial:     00:25:d3:9f:e7:48
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:    
broadcast    =    yes
driver    =    ath9k
driverversion    =    3.2.0-39-generic
firmware    =    N/A
ip    =    192.168.0.6
latency    =    0
link    =    yes
multicast    =    yes
wireless    =    IEEE 802.11bgn
resources:    
irq    :    17
memory    :    febf0000-febfffff
```
Anyone got an idea how to make wireless work with get-iplayer?
What about turning off IEEE 802.11n networking and using only b or g, which it appears can help connections for other makes of adapters, and if so, how do I do it just for that adapter, not the whole network?

---

### Post by ajgreeny on 2013-06-29
I think I have solved this problem by doing what is shown on post 6 of the thread at [http://ubuntuforums.org/showthread.php?t=1877120](http://ubuntuforums.org/showthread.php?t=1877120) which makes the atheros wireless card use software encryption instead of hardware encryption.

Suddenly I can use get-iplayer on wireless as well as cabled connection and I didn't have to disable 802.11n networking.

---

