---
title: "wireless  not working in 10.04"
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by ramsubbu on 2011-12-05
I have a DELL Vostro 1310. While wireless and lan work nicely in 9.10, they dont seem to work in 10.04. I have tried all suggestions but nothing seems to work. Posting below some of tries and outputs:

sudo lshw -C network output:
*-network               
       description: Wireless interface 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: eth2 
       version: 01 
       serial: 00:24:2b:c6:97:ad 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:19 memory:f4000000-f4003fff 
  *-network DISABLED 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:07:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:21:70:d6:2d:3a 
       size: 10MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s 
       resources: irq:28 ioport:5000(size=256) memory:f8610000-f8610fff(prefetchable) memory:f8600000-f860ffff(prefetchable) memory:f8620000-f862ffff(prefetchable) 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: vboxnet0 
       serial: 0a:00:27:00:00:00 
       capabilities: ethernet physical 
       configuration: broadcast=yes multicast=yes
For iwconfig:
lo        no wireless extensions. 
eth0      no wireless extensions. 
eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0 
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 
vboxnet0  no wireless extensions. 
pan0      no wireless extensions. 

nm-applet gives
another instance is already running. . .

For the command sudo service network-manager stop, the response is
network-manager stop/waiting
For the command sudo service network-manager start,the response is
network-manager start/running, process 1772

---

### Post by oldtimer7777 on 2011-12-05
Have you tried it in 11.10 the latest version of Ubuntu yet?

> **ramsubbu said:**
> I have a DELL Vostro 1310. While wireless and lan work nicely in 9.10, they dont seem to work in 10.04. I have tried all suggestions but nothing seems to work. Posting below some of tries and outputs:

sudo lshw -C network output:
*-network               
       description: Wireless interface 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: eth2 
       version: 01 
       serial: 00:24:2b:c6:97:ad 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:19 memory:f4000000-f4003fff 
  *-network DISABLED 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:07:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:21:70:d6:2d:3a 
       size: 10MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s 
       resources: irq:28 ioport:5000(size=256) memory:f8610000-f8610fff(prefetchable) memory:f8600000-f860ffff(prefetchable) memory:f8620000-f862ffff(prefetchable) 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: vboxnet0 
       serial: 0a:00:27:00:00:00 
       capabilities: ethernet physical 
       configuration: broadcast=yes multicast=yes
For iwconfig:
lo        no wireless extensions. 
eth0      no wireless extensions. 
eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0 
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 
vboxnet0  no wireless extensions. 
pan0      no wireless extensions. 

nm-applet gives
another instance is already running. . .

For the command sudo service network-manager stop, the response is
network-manager stop/waiting
For the command sudo service network-manager start,the response is
network-manager start/running, process 1772

---

