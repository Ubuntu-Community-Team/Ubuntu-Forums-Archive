---
title: "Wireless connection disconnects and reconnects randomly"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by Kryzzalid on 2011-12-04
Hi!
Like the title says my wireless connection disconnects and reconnects randomly. And if the connection cannot be made after a while the computer asks the wep key. And after that i can't connect anymore unless i reboot... I never had that problem before the update from 11.04 to 11.10. I don't know what specs i should put but my computer is a pavilion zv6000. It has a wireless card 802.11bg which uses a Broadcom 4306 chipset. The router is a buffalo WHR-HP-G300N.

```

lshw -C network gives:
*-network:0
description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:9 memory:b0204000-b0205fff
*-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:90:4b:a6:ae:1f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-13-generic firmware=508.1084 ip=192.168.11.2 link=yes multicast=yes wireless=IEEE 802.11bg

iwconfig wlan0 gives:

wlan0     IEEE 802.11bg  ESSID:"XXXXXXXXXXXXXX"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:A5:14:E1:41   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:80  Invalid misc:665   Missed beacon:0


```

Any help would be great. Thank you!

---

