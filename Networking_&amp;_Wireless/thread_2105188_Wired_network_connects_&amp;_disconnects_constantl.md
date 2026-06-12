---
title: "Wired network connects &amp; disconnects constantly"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by jasonlinux on 2013-01-15
Hi, I have a dual boot, Ubuntu 12.10 with win 7.

The wired network connects & disconnects ever 2 seconds. 
I have tried setting the ipv4 to link Local only and ipv6 to ignore, which stops the disconnecting, but it doesn't connect to the internet. Manually configuring didn't help either. 
Another colleague (different laptop) has no trouble, and net worked on Ubuntu just by plugging in the lan cable.
Net is working fine on USB mobile internet (MTS India)


Output from sudo lshw -C network - This is with the mobile net active and no Lan cable attached.
PCI (sysfs)  
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 70:f3:95:6f:df:c7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90100000-9010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:40:9e:4a
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:90010000-90010fff memory:90000000-9000ffff memory:90020000-9002ffff

---

