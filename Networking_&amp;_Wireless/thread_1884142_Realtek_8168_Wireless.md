---
title: "Realtek 8168 Wireless"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by electricman94 on 2011-11-20
I have a realtek rtl8168D/811D wireless card.  I need to connect to the Internet with it and it says that there is firmware missing.  I looked at some forums and was told to use this command " sudo lshw -C network.
I got this back

 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:0e:24:4b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:41 ioport:ce00(size=256) memory:fbdff000-fbdfffff memory:fbdf8000-fbdfbfff memory:fbd00000-fbd1ffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:19 memory:fbbfe000-fbbfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:a1:3e:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

I am new to ubuntu so please make the instructions simple.  How do I connect to my wireless network?  The system is a dual boot with a windows 7 32-bit.  my ubuntu os is 11.10 64-bit

---

### Post by praseodym on 2011-11-20
Hi,

the Realtek card is for wired. For your wireless Broadcom card you need to install the firmware packages **b43-fwcutter** and **firmware-b43-installer** in the software center via cable connection.

---

