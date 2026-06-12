---
title: "On board network card is not being recognized"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by Key-Tech on 2009-01-06
Hi Guys,

I'm using ubuntu 8.10 and I have two network cards installed. One is the on board lan (Intel e100/pro comes with ASUS P5GD1-VM motherboard) and the second is a PCI one. While the PCI card works fine the internal does not. 
I've got only eth0 showing up and it is related to the PCI card. I've attached the output of the dmesg file. In it I see that the internal card is detected but have the same eth as the PCI card.
If you can help understand how to load the intel driver so I will have eth0 and eth1.
  Thanks in advance

Following is a portion of dmesg file that I think is relevant:

[SIZE="1"][    2.741901] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
.
.
[    3.180461] 8139cp 0000:01:0a.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.180467] 8139cp 0000:01:0a.0: Try the "8139too" driver instead.
.
.
[    3.520964] 8139too 0000:01:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.521800] eth0: RealTek RTL8139 at 0xa800, 00:1d:0f:c0:38:33, IRQ 22
[    3.521804] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
.
.
[   29.408008] eth0: no IPv6 routers present
.
.
[ 1201.519933] eth0: link down
[ 1270.747045] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
.
.
[ 3519.590027] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3530.044018] eth0: no IPv6 routers present
[ 4402.319086] Intel(R) PRO/1000 Network Driver - version 7.3.20-k3-NAPI
[ 4402.319095] Copyright (c) 1999-2006 Intel Corporation.
[ 4465.540306] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[ 4465.540314] e100: Copyright(c) 1999-2006 Intel Corporation
[/SIZE]

---

### Post by Key-Tech on 2009-01-06
Ok, I've got here some extra info, hope it will help you to help me:

[SIZE="1"]sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=56 mingnt=8
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: eth0
       version: 10
       serial: 00:1d:0f:c0:38:33
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.22 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:21:96:3c:80:5b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/SIZE]

---

