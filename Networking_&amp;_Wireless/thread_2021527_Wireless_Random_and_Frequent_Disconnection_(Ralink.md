---
title: "Wireless Random and Frequent Disconnection (Ralink Card)"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by PM5K on 2012-07-09
Hello,

I wanted to ask for some assistance in, perhaps, solving an annoying issue. My Wi-Fi seems to disconnect very often since I first installed Ubuntu (Last friday).

The issues is not AP dependent as I have tried this with various access points... I have read many(at least 20...) threads about possible fixes by removing ubuntu network manager and using WICD instead, but either I have not done it properly or it did not work...

Being a new Ubuntu (Linux for that matter) user, I am unfamiliar with what information I should present when asking for help (logs, dumps, etc...);

I humbly ask for any assistance you may be able to provide as I am at my wits end here... :(

lshw dump in case more info on card is needed can be found below.

Thank you.

> anonymous@APC:~$ sudo lshw -C network
[sudo] password for anonymous: 
  *-network               
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:24:00.0
       logical name: wlan0
       version: 00
       serial: 9c:b7:0d:90:e5:6e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-26-generic firmware=0.34 ip=10.33.17.86 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:d4700000-d470ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:25:00.0
       logical name: eth0
       version: 06
       serial: e4:11:5b:45:3e:76
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:52 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff


---

