---
title: "networking stops working after suspend/hibernate on Ubuntu 10.10"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by arclinux on 2010-10-22
networking stops working after suspend/hibernate on Ubuntu 10.10 and it used to happen on 10.04 though i did not bother to resolve the issue then 

output of sudo lshw -C network 
-------------------------------

*-network DISABLED 
description: Wireless interface
product: AR9285 Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:08:00.0
logical name: wlan0
version: 01
serial: 00:24:2c:6a:8d:27
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 memory:d1200000-d120ffff
*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 03
serial: 00:23:8b:c5:eb:75
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.24.16.40 latency=0 link=yes multicast=yes port=MII speed=100MB/s
resources: irq:45 ioport:2000(size=256) memory:d1004000-d1004fff memory:d1000000-d1003fff memory:d1010000-d101ffff
---------------------------------------------------

---

### Post by kiitii on 2011-04-05
I am using Lenovo thinkpad x100e with Ubuntu 10.10 netbook edition.

I am facing same problem, after wake up from suspend, my Wired & Wireless network cannot function.

Here's the output after rebooting my notebook.

linus@inspirebuntu:~$ sudo lshw -C network
[sudo] password for linus: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:55:94:b5
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:a000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff memory:d0020000-d003ffff
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 90:4c:e5:e2:22:61
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=V 1.1 firmware=49 ip=192.168.100.2 latency=0 link=yes multicast=yes wireless=802.11bgn
       resources: irq:18 ioport:b000(size=256) memory:d0300000-d0303fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes



Help please!

---

