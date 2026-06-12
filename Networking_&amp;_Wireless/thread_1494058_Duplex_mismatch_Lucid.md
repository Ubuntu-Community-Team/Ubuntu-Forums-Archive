---
title: "Duplex mismatch Lucid"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by xflyboy on 2010-05-26
Had a issue with fresh install of Ubuntu 10.04.
My network conection was rather slow. Tried to do a File Transfer over SFTP on LAN 100 MB network and was able to archive only 300Kbps (or something like that KB, Kb), well, it was sloowww..
Tried to do it over Crosed Wire and archived 1,5 Mbps.

So, went to check CISCO Switch Settings and noticed a lot of CRC, Drops, and collisions on both Interfaces. Both settings were set to FUll Duplex, 100Mbps on the switch, but did not found what duplex were set on Network Card. - So started to look for commands to check that.

So, tried to disable IP6 (even it have nothing to do) - Will not hurt. And before resart, found that both interfaces were Half Duplex.

So with [this guide]("http://jaxov.com/2009/09/change-ethernet-cards-speed-and-dulex-settings-in-ubnutu-linux/") changed their Duplex to Full and problem went away.

max@dc7800:~$ uname -a
Linux dc7800 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
max@dc7800:~$ sudo lshw -C network
[sudo] password for max: 
  *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 02
       serial: 00:0f:fe:90:f7:9a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 **duplex=half** firmware=1.3-1 ip=x.x.x.x latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:f0180000-f019ffff memory:f01a5000-f01a5fff ioport:2100(size=32)
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:07:09.0
       logical name: eth0
       version: 78
       serial: 00:04:75:d0:14:ee
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=3c59x **duplex=full** ip=x.x.x.x latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:1100(size=128) memory:f0200000-f020007f memory:c0800000-c081ffff(prefetchable)


Though still not able to get Full Dupplex from eth1 82566DM-2 Gigabit Network Connection

---

### Post by xflyboy on 2010-05-26
sudo ethtool -s eth1 autoneg off duplex full
did the trick setting eth1 to full duplex.

max@dc7800:~$ sudo mii-tool 
eth0: 100 Mbit, full duplex, link ok
SIOCGMIIREG on eth1 failed: Input/output error
SIOCGMIIREG on eth1 failed: Input/output error
eth1: 100 Mbit, full duplex, link ok

---

### Post by xflyboy on 2010-05-27
Doing Remote Admin by Neatx and at this moment can not change any interface by Network Manager. "Edit" option is grayed and not clickable.
Is it because i have changed Interface settings manualy?
Regards.

---

