---
title: "wireless UNCLAIMED, fresh 10.10 install"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by cytg on 2011-01-15
Hi, trying to get 10.10 running on oldish laptop Fujitsu Amilo L1300 series..

Heres lshw -C network

  *-network:0 UNCLAIMED   
       description: Network controller
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
       resources: memory:e0002000-e0003fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 10
       serial: 00:40:d0:64:35:c2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.193 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:3 ioport:c100(size=256) memory:e0000000-e00000ff


I've googled around and have not come to anything conclusive... ideas ?
Thanks!

---

### Post by chili555 on 2011-01-15
I believe this device is supposed to work with the driver p54pci, however it requires firmware. While you have an ethernet connection, please do:```
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet cable, reboot and give us your report.

---

