---
title: "Need wireless help please"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by HIjustme on 2009-02-27
HI all, just registered, thought i'd be needing to post a few questions here in the future as im pretty new to ubuntu/linux.

First of all i'd like to ask how I can start my wireless connection without booting up windows, then restarting and booting ubuntu to get the connection.
Heres some info about my connection if it helps...

Interface : 802.11 WiFi (wlan0)
Driver : rt2400pci
Speed 1mb/s(on windows i always get 11mb/s =[ )

00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:05.0 Network controller: RaLink Wireless PCI Adapter RT2400 / RT2460
01:07.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
01:0d.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

Thanks.

---

### Post by HIjustme on 2009-03-04
Heres more info, please help if anyone has any idea's.
Thanks.

```
*-network:0             
       description: Wireless interface
       product: Wireless PCI Adapter RT2400 / RT2460
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wmaster0
       version: 00
       serial: 00:11:09:08:18:f6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2400pci ip=192.168.1.64 latency=32 module=rt2400pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 01
       serial: 00:11:09:fc:a2:5f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
```

---

### Post by HIjustme on 2009-03-08
up

---

