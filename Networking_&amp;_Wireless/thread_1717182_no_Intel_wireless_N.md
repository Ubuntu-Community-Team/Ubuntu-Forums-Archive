---
title: "no Intel wireless N"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2011-03-29
Does this imply my 'N' card is not 'N' or maybe the software is old?
I bought it on ebay.


$ sudo lspci
03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300

$ sudo iwconfig
wlan1     IEEE 802.11abg

$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 00
       serial: 00:21:6a:77:b6:e2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-28-generic firmware=8.24.2.12 ip=192.168.1.132 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:75200000-75201fff

---

