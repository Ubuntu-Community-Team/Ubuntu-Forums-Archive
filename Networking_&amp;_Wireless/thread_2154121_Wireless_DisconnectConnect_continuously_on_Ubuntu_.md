---
title: "Wireless Disconnect/Connect continuously on Ubuntu 13.04"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by rac4299 on 2013-06-13
I have a problem with the wireless. It connects to my wireless and it works for a minute or 2 and then disconnects and autmatically reconnects, works for a minute and then disconnect again.

Sometimes I need to turn off the wireless and back on again to make it work. Any ideas?

Here is some info:

lshw -C network
  *-network               
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: f4:b7:e2:92:56:1d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-23-generic firmware=0.37 ip=192.168.50.79 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c0610000-c061ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: 74:46:a0:53:2b:74
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff

---

### Post by campos20 on 2013-07-17
I have the same problem. Strangely, when I use ubuntu 12.04 and the [Richard Rickets's solution for RT3290]("http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/"), everything works just fine.

---

