---
title: "HP Pavilion wireless worked; and then it didn't"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by jalandoak on 2009-07-05
Hello.  I installed Ubuntu 9.04 using Wubi, and figured out how to get wireless working by activating b43-fwcutter in Hardware Drivers.  Three days aga, the updage manager prompted me to upgrade, and restart.  I havn't gotten the wireless to work since.  I reinstalled b43-fwcutter, which didn't produce any errors, but it doesn't show in Hardware Drivers any longer to activate it.  Any help would be appreciated.

Running "lspci" from the terminal procudes:

06:02.0 Network controller [0280]: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)

Running "lshw -C network" from the terminal produces:

  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:3c:80:78
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 82:d7:fb:e7:49:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I've gone through several threads here and on other sites, but haven't had any luck.  This is frustrating because it did work.  Any help would be appreciated.

Jeff

---

