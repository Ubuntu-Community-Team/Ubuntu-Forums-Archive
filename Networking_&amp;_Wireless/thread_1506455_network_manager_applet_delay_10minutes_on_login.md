---
title: "network manager applet delay 10minutes on login"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by dcfmarcos on 2010-06-10
Last night a begin experience problems with network manager. Everything was working fine. But now network manager applet delays like 10 minutes to appear, network connection freeze when I open it (system/preference/network connections) or from network manager applet. When login both panel top and bottom delay 20sec in appear. I had search for hours and the fix the give like **nm-applet --sm-disable** not work for me. I want to know is there a way for reinstalling network connections to default configuration.

[B][I]Any help will be appreciated
Thanks[/I][/B]

Im using Ubuntu 10.04lts 64bits. In Hp dv5 pavilion.
Some info using command: **lshw -class network** 
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4d:6a:d2:62
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet  physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:d1100000-d110ffff

  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:dd:b8:60
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.41.77.89 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d102ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by nipepusy on 2010-06-11
I have the same problem - did work previously - now takes 10 min+ to connect.

Asus M600 Ubuntu 10.04

*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth0
       version: 10
       serial: 00:13:d4:50:82:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:5 ioport:e800(size=256) memory:fdd00000-fdd000ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:a6:b5:62
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.0.196 latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:4 memory:fdc00000-fdc00fff

Also Network Connections freezes - whether wireless connected or not

Would appreciate any help

---

### Post by therman on 2010-06-12
I have the same problem. I have encountered this the first time yesterday.
Could this be because of an update?

---

