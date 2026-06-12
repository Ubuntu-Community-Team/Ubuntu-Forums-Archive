---
title: "HP Pavilion dv7-1264nr"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by StephenOK on 2010-04-08
Hi folks:

This is what I've gathered from terminal:

  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:68:00:e5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d1100000-d110ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:25:1e:77
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d103ffff(prefetchable)
stephen@stephen-laptop:~$ 

I finally wiped Vista off the machine and now it's an exclusively Ubuntu
9.10 laptop. Can't wait to dig into Ubuntu Studio! However, I'm having some connectivity issues: The wireless connection isn't that great on my HP, but it's awesome on my Mac Book Pro.

Are there any drivers that I can download to fix this issue? Or can I simply gather a proper driver off the Ubuntu install CD?

Any help would be greatly appreciated.

Thanks in advance,

Steve

---

### Post by chili555 on 2010-04-08
> The wireless connection isn't that great on my HP,Can you be a little more specific? What are the symptoms? Please post:```
iwconfig wlan0
```Thanks.

---

