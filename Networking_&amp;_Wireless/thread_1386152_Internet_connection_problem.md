---
title: "Internet connection problem"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by chris0108 on 2010-01-20
Hi there, im new to ubuntu and im having a problem connecting my laptop to the internet, its a samsung v20 laptop the wireless connection is via a belkin f5d7010 wireless pci card. Ubuntu finds the card ok but first of all couldnt connect at all, iv done a bit of research and used ndiswrapper to install the windows driver for it, it now goes to the point of where the network light comes on but it wont connect, i know the password is correct (another laptop uses the same connection), just wondered if anyone had any ideas?

Many thank for any help offered

---

### Post by Iowan on 2010-01-20
From a terminal, post results of **ifconfig -a** and **sudo lshw -C network**. Ask if you need help with terminal, posting, etc.

---

### Post by chris0108 on 2010-01-20
ifconfig reads -

eth0      Link encap:Ethernet  HWaddr 00:00:f0:6e:3e:1e  
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::200:f0ff:fe6e:3e1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1826 (1.8 KB)  TX bytes:5463 (5.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:30:4c:2a  
          inet6 addr: fe80::217:3fff:fe30:4c2a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:378 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1045095 (1.0 MB)  TX bytes:44997 (44.9 KB)
          Interrupt:10 Memory:28000000-28000025 

sudo lshw -c network reads -

  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:00:f0:6e:3e:1e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.2.9 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:d0104000-d0104fff ioport:3000(size=64)
  *-network
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 20
       serial: 00:17:3f:30:4c:2a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+blkwgnv7 driverversion=1.55+Belkin,10/19/2006,5.87.19.1 latency=64 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: irq:10 ioport:3400(size=256) memory:28000000-280003ff

---

### Post by Iowan on 2010-01-20
What happens if you don't have the wire plugged in? (eth0 has an IP address, and NM will ordinarily manage only one interface at a time)

---

### Post by chris0108 on 2010-01-20
Its strange to be honest, there are two lights on the belkin card, the signal one flashes like normal, the network one does now light up but it only does it for a very short time then tells me it has disconnected.

I know the password is correct as another laptop uses the same network, the card was working fine too. It just looks as though the password is wrong

---

