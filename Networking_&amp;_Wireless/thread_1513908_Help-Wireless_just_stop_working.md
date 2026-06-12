---
title: "Help-Wireless just stop working"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by hoboy on 2010-06-20
I remember that my wireless was working, but I have just noticed that when I click on Network icon on the top right corner of the ubuntu panel only wired Network auto eth0 is active.
There is no active wireless.
Wireless Network is not active, I know it has worked before.

test@test-desktop:~$ sudo lshw -C network
[sudo] password for test: 
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:24:21:10:ed:af
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.11 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:28 memory:f9e77000-f9e77fff ioport:b880(size=8) memory:f9e7e800-f9e7e8ff memory:f9e7e400-f9e7e40f
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:43:3a:98:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
test@test-desktop:~$ sudo lshw -C network
[sudo] password for test: 
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:24:21:10:ed:af
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.11 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:28 memory:f9e77000-f9e77fff ioport:b880(size=8) memory:f9e7e800-f9e7e8ff memory:f9e7e400-f9e7e40f
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:43:3a:98:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
test@test-desktop:~$

---

