---
title: "wireless not working on new install of 9.1"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by bfever74 on 2010-02-01
I'm about to pull my hair out.  Have spent 6-8 hours trying to get the darn wireless to work.  Started on Network Manager, switched to WICD, then back to Network manager.  Have uninstalled and reinstalled driver a dozen times. When I go to System->Administration->Windows Wireless Drivers, get pop-up saying "Unable to see if hardware is present"  When I click "OK" then network driver window says "Hardware present: Yes" and the driver is listed.  

First time user of Linux, and getting frustrated.  I really want this to work so I can become as smart as all of you reading this post.  Thanks!!!

bret@novus-laptop:~$ sudo lshw -c network
[sudo] password for bret: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:e4:b9:92
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.17 ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:fc500000-fc50ffff

---

### Post by bfever74 on 2010-02-01
I'm a noob, and I really need help!!!!

---

### Post by nooblinuxuser0231 on 2010-02-01
sure you don't have multiple ethernet drivers running at the same time? did you check with lsmod?

---

### Post by bfever74 on 2010-02-01
I don't know if I have multiples running or not, and I don't know what ismod is.  I'm a noob

---

