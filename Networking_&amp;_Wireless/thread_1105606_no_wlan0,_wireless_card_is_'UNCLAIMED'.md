---
title: "no wlan0, wireless card is 'UNCLAIMED'"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by andrewwg94 on 2009-03-24
so the other day i installed the xubuntu-desktop package. after i restarted. my wireless stopped working. i realized that i no longer have a 'wlan0'. i use the b43 fwcutter driver which comes with ubuntu. when i did lshw -C network, i got a big 'unclaimed' next to my wireless card. how do i fix this? and is there anyway to fix it without a live connection to the internet? (but i can download a package from windows and save it on the ubuntu partition).

i'm on i386 ubuntu 8.10

---

### Post by andrewwg94 on 2009-03-29
.

---

### Post by andrewwg94 on 2009-03-29
bump, here's lshw:

```
andrew@andrew-laptop:~$ sudo lshw -C network
[sudo] password for andrew: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:42:8d:61
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.15.102 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f6:5b:fb:e7:29:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
andrew@andrew-laptop:~$ 

```

---

