---
title: "new install of ubuntu 12.04 lts on DELL LATITUDE D610 - WLAN Issue"
date: 2012-10-06
forum: Networking &amp; Wireless
---

### Post by DocThunderbird on 2012-10-06
I have installed 12.04 on a DELL LATITUDE D610 but cannot get the wireless card to enable.  I have tried to install the drivers "bcwml5.inf" with no success.

below is the output of lshw -C network

kaitlyn@KO:~/bcm43xx$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:06:24:50
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5751-v3.29a ip=192.168.1.11 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:dfcf0000-dfcfffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfbfe000-dfbfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:4b:09:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-31-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
kaitlyn@KO:~/bcm43xx$

---

### Post by chili555 on 2012-10-06
Please temporarily hook up the ethernet and do:```
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

---

