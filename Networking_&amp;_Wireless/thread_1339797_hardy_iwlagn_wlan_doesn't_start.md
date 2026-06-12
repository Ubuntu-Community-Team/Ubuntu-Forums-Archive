---
title: "hardy iwlagn wlan doesn't start"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by nafihsus on 2009-11-27
I am following the [WirelessTroubleShooting]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") Guide to solve my WLAN [problem]("http://ubuntuforums.org/showthread.php?t=1270799"). Hardware and driver seem to be ok but I can't get the network started. lshw output is

```
           *-network DISABLED
                description: Wireless interface
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:18:00.0
                logical name: wmaster0
                version: 00
                serial: 00:21:5d:a2:25:e6
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.2.98 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```
I booted Vista on the same laptop and WLAN worked instantly, assuring the wlan hardware switch is in the right position.

Any idea what I could try next?

---

