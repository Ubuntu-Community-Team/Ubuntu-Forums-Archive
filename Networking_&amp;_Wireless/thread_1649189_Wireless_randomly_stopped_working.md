---
title: "Wireless randomly stopped working"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by VTBuc on 2010-12-19
So I'm using a starling netbook which worked perfectly fine for about the first 5 months I owned it. Last night, I started having problems. I came home and it was having difficulties connecting to my home wireless network. It would start connecting and then drop the connection. i tried rebooting, and it only got worse. Now, the wireless card doesn't recognize anything. When I click the network icon it doesn't find any wireless networks(there's about 10 in-range here). I tried doing system restore with System76 driver but that didn't help.

Any advice?
sean@sean-laptop:~$ sudo lshw -C network
[sudo] password for sean: 
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 10
       serial: 74:f0:6d:27:45:c4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:09:00.5
       logical name: eth0
       version: 02
       serial: 00:90:f5:a6:6b:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 memory:f0200000-f0203fff ioport:3400(size=128) ioport:3000(size=256)
sean@sean-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

edit: Oh, and the wireless light is on indicating that it ought to be working. And I'm using 10.04 netbook remix. Thanks!

---

