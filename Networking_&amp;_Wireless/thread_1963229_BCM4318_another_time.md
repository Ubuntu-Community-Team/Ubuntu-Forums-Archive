---
title: "BCM4318 another time"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by ReeDeMeR on 2012-04-22
hi guys, i read these treads many time n i try several method to make my wireless card working. so many.
now i ask for help. 2 days ago, at my work place i finally powned this wifi, but, back to home it died another time.
so problem is: pc desktop, card is the famous BCM4318 with driver b43, the device cant scan (also at my work place, but putting in the right information he could get stable connection, at home nothing worked) 
so this is the output for lshw```
id:network
                   description: Network controller                 product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller                 vendor: Broadcom Corporation                 physical id: 1
                 bus info: pci@0000:05:01.0
                 version: 02                 width: 32 bits                 clock: 33MHz                 capabilities: bus_master                  configuration: driver=b43-pci-bridge latency=32                 resources: irq:22 memory:70004000-70005fff
```
and the second one, in red is ```
id:network
          description: Wireless interface        physical id: 1
        logical name: wlan0
        serial: 00:11:50:f5:da:9e        capabilities: ethernet physical wireless         configuration: broadcast=yes driver=b43 driverversion=3.0.0-17-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```then, iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

---

### Post by wildmanne39 on 2012-04-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

