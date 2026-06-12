---
title: "Wireless Switch Karmic"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by su-37 on 2010-02-12
hey Upgraded to 9.04 then 9.10 in a bid to get wireless working and it seems not to want to. this is the information i have managed to gather.
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:1f:16:57:b6:cc
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list rom ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.9 latency=0 multicast=yes
resources: irq:28 ioport:3000(size=256) memory:93010000-93010fff(prefetchable) memory:93000000-9300ffff(prefetchable) memory:93020000-9303ffff(prefetchable)


*-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wmaster0
version: 01
serial: 00:24:2b:24:83:80
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:17 memory:95100000-9510ffff


Also in the notification area, when i click on the network icon the wired network comes up fine but not the wireless.

---

### Post by chili555 on 2010-02-12
Your wired interface:> ip=192.168.0.9 > when i click on the network icon the wired network comes up fine but not the wireless. Please see: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

Especially see:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themPlease detach the wire and see if the wireless is now available.

The details about your wireless look just fine, like it's ready to go as soon as Network Manager starts it.

---

