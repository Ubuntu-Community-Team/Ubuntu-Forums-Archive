---
title: "Wired connection not working"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by kcfd25 on 2011-01-07
I originally posted this in the beginners forum but thought it would be better suited in this one.  Been doing hours of research trying to solve this problem with no luck.
Running a wired connection through a Linksys router that suddenly stopped working today.  I thought this was a ipv6 issue sinced I enabled some of those settings to share a connection with my PS3.  I have since disabled IPv6 in Firefox and through the grub.  The RealTek adapter will not even show a connection through the network manager when connected.  The onboard adapter will show a connection, give me a ip address and MAC but still will not load the internet.  I've tried uninstalling and reinstalling both adapters through the network connections, as well as reinstalling Firefox to no avail.  I've also tried using Open DNS servers.   I cannot ping through the network tools either. Hard for me to paste a ifconfig since I'm on my laptop.  I'm running Ubuntu 10.10 (not dual booting).  I did some updates this morning but it worked fine for a little while after that, until I tried to connect to my PS3  Any help would be appreciated.  Thanks.

---

### Post by PatchesTheCaveman on 2011-01-07
> I did some updates this morning but it worked fine for a little while

Until you rebooted perchance?  There's a bad update going around that's causing problems with many devices.  You can see if you have it and fix it by following the instructions I provided in this post:
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

---

### Post by kcfd25 on 2011-01-08
[FONT=&quot]Just checked the kernel.  Its not the bad one.  Found my usb stick.:)  Was able to copy over ifconfig and lshw -c.  Any help is appreciated. 
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]ifconfig

eth0 Link encap:Ethernet HWaddr 00:1b:fc:a9:e0:e9 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Memory:dbfc0000-dc000000 

eth1 Link encap:Ethernet HWaddr c8:3a:35:d3:60:e8 
inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:10 errors:0 dropped:0 overruns:0 frame:0
TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1166 (1.1 KB) TX bytes:2699 (2.6 KB)
Interrupt:21 Base address:0xc00 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2424 errors:0 dropped:0 overruns:0 frame:0
TX packets:2424 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:219124 (219.1 KB) TX bytes:219124 (219.1 KB)



sudo lshw -C network


*-network 
description: Ethernet interface
product: L2 Fast Ethernet
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: a0
serial: 00:1b:fc:a9:e0:e9
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 firmware=L2 latency=0 link=no multicast=yes port=twisted pair
resources: irq:40 memory:dbfc0000-dbffffff memory:dbfa0000-dbfbffff
*-network
description: Ethernet interface
product: RTL-8169 Gigabit Ethernet
vendor: Realtek Semiconductor Co., Ltd.
physical id: 1
bus info: pci@0000:01:01.0
logical name: eth1
version: 10
serial: c8:3a:35:d3:60:e8
size: 10MB/s
capacity: 1GB/s
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
resources: irq:21 ioport:b800(size=256) memory:dbeffc00-dbeffcff memory:dbec0000-dbedffff

 [/FONT]

---

### Post by kcfd25 on 2011-01-08
Figured out the problem.  I just shut everything down and unplugged everything.  It has something to do with my PS3 being connected to my onboard ethernet.  As soon as I turn it off the internet stops working.  I'm basically trying to use on NIC for internet and one as a local link.

---

