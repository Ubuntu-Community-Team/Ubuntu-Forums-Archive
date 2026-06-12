---
title: "Wired networking problem"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by devobitch on 2010-05-03
i cant get wired networking to work either
this a dual boot with win xp which works fine and ubuntu 9.10
worked fine

aaron@ubuntu-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:31:77:dc:4a  
          inet addr:192.168.1.175  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe77:dc4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1067 (1.0 KB)  TX bytes:4382 (4.3 KB)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:808 (808.0 B)  TX bytes:808 (808.0 B)

@ubuntu-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:17:31:77:dc:4a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.175 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:e400(size=256) memory:ff6fb000-ff6fbfff memory:ff6c0000-ff6dffff(prefetchable)


it looks ok to me but i cant ping from a another box or in i try to ping from ubuntu net tools it just dissapears

this was a clean in stall on sepperate hard drive

any help 

devobitch

---

### Post by Iowan on 2010-05-03
Moved to it's own thread.
 Debugging can be directed to solve YOUR problem.

---

