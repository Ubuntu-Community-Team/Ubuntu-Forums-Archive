---
title: "why my wireless interface is eth0 why not wlan0"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by bengaltiger on 2010-05-10
Hi,

I my netbook (HP mini 2140) has ubuntu 10.04. (netbook remix)

Conky 1.8.0 compiled Fri Apr 23 10:38:37 UTC 2010 for Linux 2.6.24-27-server (i686)

eth0 is for wireless and eth1 for ethernet and wireless is workig fine.

I could not get it any wirless variables in conky. like wireless_link_qual wireless_link_bar etc.

some info...
iwlist scan
lo Interface doesn't support scanning.
eth1 Interface doesn't support scanning.
eth0 Interface doesn't support scanning.

*-network
description: Wireless interface
product: BCM4322 802.11a/b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:08:00.0
logical name: eth0
version: 01
serial: 00:21:00:d3:cf:74
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.*.* latency=0 multicast=yes wireless=IEEE 802.11
resources: irq:16 memory:e8000000-e8003fff

my Q is why my wireless interface is eth0 why not wlan0?

How I can get wireless_link_qual wireless_link_bar SSID , signal strength values?

Thanks,
BT

---

### Post by Iowan on 2010-05-10
My laptop (also an HP) uses **eth0** for wired and **eth1** for wireless. Yes, it's curious, but works - so I haven't tried to change it.
You might be able to change it in */etc/udev/rules.d/70-persistent-net.rules*

---

### Post by bengaltiger on 2010-05-11
one interesting thing,

if run iwconfig this is the output.
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:213  Noise level:171
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

but if I run iwconfig with sudo then detailed info of etho is coming.

is it right?

BT

---

