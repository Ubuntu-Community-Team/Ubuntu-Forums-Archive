---
title: "ETH0 fails after suspend"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by Andy17MB on 2010-10-14
Hi, after reading numerous posts and getting nowhere I am posting this whilst I still have hair left to pull out..  I (foolishly) suspended my desktop and now can not get a network connection.  I am running Ubuntu 10.04 32 bit on an Athlon 64 3500+ based system that has run fine until now. The router is fine.

I have tried various suggestions and the result of the most revealing one is attached

> atc@atc-desktop:~$ sudo lshw -C network
[sudo] password for atc: 
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:15:58:4c:63:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:f000(size=256) memory:dffff000-dffff0ff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
atc@atc-desktop:~$ sudo ifconfig eth0 down
atc@atc-desktop:~$ sudo ifconfig eth0 up
atc@atc-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
atc@atc-desktop:~$

Even after all of this I still can not get the network up and running.  Any suggestions would be appreciated

Andy

---

