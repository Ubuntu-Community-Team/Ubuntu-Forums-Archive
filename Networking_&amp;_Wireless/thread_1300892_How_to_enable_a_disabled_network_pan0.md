---
title: "How to enable a disabled network pan0"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by redb on 2009-10-25
I have been trying and trying to get a wifi cardbus up and running with no luck.  I have another wireless card installed but would like to be able to use this ralink bus card if I can.  any help?

```
 *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-network UNCLAIMED
          description: Network controller
          product: RT2760 Wireless 802.11n 1T/2R Cardbus
          vendor: RaLink
          physical id: 0
          bus info: pci@0000:0c:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0 maxlatency=4 mingnt=2
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:ef:ba:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:5d:1f:f1:6b:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

