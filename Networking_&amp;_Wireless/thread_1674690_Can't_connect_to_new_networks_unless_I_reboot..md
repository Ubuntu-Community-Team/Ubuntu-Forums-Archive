---
title: "Can't connect to new networks unless I reboot."
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by fiacobelli on 2011-01-24
Hi,
I have an hp dm1z and ubuntu 10.10 64bit. 
My problem: After I suspend (close the lid) and wake it up (open the lid) at a different location with a network connection (wired or wireless), my system always fails to connect. I need to reboot and then it sees the network and connects fine. 

I have tried /etc/inet.d/networking restart, but nothing changes.

The only exception to this rule are two networks that have WPA security settings and are stored. I can always switch between those two.

I have tried ifconfig eth0 up & down and restart networking. I have also tried to connect manually  (dhclient) and no success. None of these work. I am including the output of lshw -C network.

Please help!!!!
thanks.

Francisco.



lshw -C network:
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 78:ac:c0:54:3f:40
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:2000(size=256) memory:f0010000-f0010fff memory:f0000000-f000ffff memory:f0020000-f002ffff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 01
       serial: e0:2a:82:46:a5:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=165.124.97.89 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f1000000-f1003fff

---

### Post by fiacobelli on 2011-01-26
Any ideas on how I can look at what exactly happens to set up the network after each reboot? What files to look at?

thanks

---

