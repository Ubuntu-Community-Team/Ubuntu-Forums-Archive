---
title: "Atheros wireless driver problem"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by Omri16 on 2010-02-06
Hi all,

I have a problem with an Atheros wireless driver (not working, under Ubuntu 8.04). Please see the following thread I opened a while ago:
[http://ubuntuforums.org/showthread.php?t=1123408]("http://ubuntuforums.org/showthread.php?t=1123408")
I did not respond to the last post in this thread because I had a lot going on at that time, and now the thread won't jump any more. Anyway, the last post there asked for the output of **sudo lshw -C network**, so here it is:
```
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:32:6d:f0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.2.101 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

```
Could you please help me? I can't use wireless networks under Ubuntu :(

Thanks!

---

### Post by Omri16 on 2010-02-06
Please people... I've also tried ndiswrapper but nothing seems to help. Please please help me, it's driving me crazy :( :(

---

### Post by rfay on 2010-02-13
I've got this on a Sony Vaio, brand new. I have a few things yet to try, and will report back if I figure anything out.

---

### Post by rfay on 2010-02-13
I was successful with my Sony F-Series using the instructions in this post: [http://forum.notebookreview.com/showthread.php?t=448894&page=228](http://forum.notebookreview.com/showthread.php?t=448894&page=228)

The gist was: Install the linux-backports-modules-wireless-generic package.

---

### Post by livelyppop on 2010-02-13
I have basically the same problem. I'm using 9.1 and can't get my wireless to turn on... the indicator shows it is off it is red instead of blue like it was with windows.... When I installed the driver it told me invalid driver. I used the .inf for it. I would like any help. I am completely new at this Ubuntu.
H *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:71300000-7130ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:29:d1:8d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.5 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:1000(size=256) memory:71200000-712000ff
ere is my sudo on it....

Thanks

---

