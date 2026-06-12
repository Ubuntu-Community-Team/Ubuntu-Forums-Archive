---
title: "Dual network card detection over 2.26.31.12 kernel"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by dvladek on 2010-05-28
Dear,

I have a problem with 82571EB Dual Server card (from Intel) detection over 9.10 Ubuntu distribution with a 2.6.31.12 kernel compiled.

The problem is that if I start-up the computer from power off state, the ubuntu don't detect and not configure my network card (but yes the other integrated Realtek Card on ASUS motherboard) In otherwise, if I reset the computer (with a reboot, switching the reset button or other kind of combination) the network card is detected.

More curious is the fact that when card is detected, seems to use the e1000e module driver (but, in fact, this modules not appear loaded) Things that i've tested:

- Upgrade the ASUS bios to the last version -> no results
- Disable e1000 driver -> no results
- Upgrade to 2.26.32 kernel -> no results
- Manual compile the e1000e Intel provided module -> no results
- Test network card (and equipment) over Windows XP -> function without any problem
- Test network card (and equipment) over last version of Fedora -> same results as ubuntu
- Swith off the ACP detecttion (first over BIOS, then over kernel and both) -> no results
- Load e1000e module manually -> no results

Next, we put the information of different comands where the network card is detected. The same comand without network card not show results about it:

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 83a3
--
07:00.0 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
	Subsystem: Intel Corporation Device 115e
--
07:00.1 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
	Subsystem: Intel Corporation Device 115e

root@de-sage1:~# ethtool -i eth3
driver: r8169
version: 2.3LK-NAPI
firmware-version: 
bus-info: 0000:03:00.0

root@de-sage1:~# ethtool -i eth4
driver: e1000e
version: 1.0.2-k2
firmware-version: 5.11-2
bus-info: 0000:07:00.0


root@de-sage1:~# ethtool -i eth5
driver: e1000e
version: 1.0.2-k2
firmware-version: 5.11-2
bus-info: 0000:07:00.1

root@de-sage1:~# uname -a
Linux de-sage1 2.6.31.12 #1 SMP PREEMPT Tue May 18 15:01:21 CEST 2010 x86_64 GNU/Linux

Dmesg
[    2.985270] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    2.985273] e1000e: Copyright (c) 1999-2008 Intel Corporation.

root@de-sage1:~# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 82571EB Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth4
       version: 06
       serial: 00:15:17:db:62:d6
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=5.11-2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:37 memory:fbd80000-fbd9ffff memory:fbd60000-fbd7ffff ioport:d880(size=32) memory:fbd40000-fbd5ffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: 82571EB Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0.1
       bus info: pci@0000:07:00.1
       logical name: eth5
       version: 06
       serial: 00:15:17:db:62:d7
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=5.11-2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:38 memory:fbde0000-fbdfffff memory:fbdc0000-fbddffff ioport:dc00(size=32) memory:fbda0000-fbdbffff(prefetchable)
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth3
       version: 03
       serial: e0:cb:4e:4e:32:3a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.48.150 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:36 ioport:a800(size=256) memory:f6fff000-f6ffffff(prefetchable) memory:f6ff8000-f6ffbfff(prefetchable) memory:fbaf0000-fbafffff(prefetchable)

Any, idea, comment, will be welkome?

Thanks very much,
dvladek

---

