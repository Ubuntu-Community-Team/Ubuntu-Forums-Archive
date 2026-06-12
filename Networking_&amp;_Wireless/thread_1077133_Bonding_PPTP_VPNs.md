---
title: "Bonding PPTP VPNs"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by ut20xx on 2009-02-22
I am trying to bond together several PPTP VPN connections to Windows PCs. I have gotten the VPNs working as ppp0 and ppp1, but I am not sure how to go about bonding them. I tried just adding 
```
auto bond0
iface bond0 inet manual
```
to my /etc/network/interfaces file and then running "ifenslave bond0 ppp0 ppp1" but it just says "Error: Enslave failed" for both ppp0 and ppp1. It also mentioned that it could not set the hardware address for bond0. Any help would be greatly appreciated, including an alternate approach to load balancing access through the two connections.

---

### Post by Crafty Kisses on 2009-02-22
First I want to see some results of a couple of commands. Does your installation support network bonding? What does this bring back?
```
grep ifenslave /sbin/ifup
```
What are the results of this command?
```
sudo gedit /proc/net/bonding/bond0
```
I also wouldn't mind seeing the following as well:
```
ifconfig
```

---

### Post by ut20xx on 2009-02-22
Here's the output of the commands you requested:
```
**jon@jon-ubuntu:~$** grep ifenslave /sbin/ifup
**jon@jon-ubuntu:~$** sudo cat /proc/net/bonding/bond0
[sudo] password for jon:
Ethernet Channel Bonding Driver: v3.2.3 (December 6, 2007)

Bonding Mode: adaptive load balancing
Primary Slave: None
Currently Active Slave: None
MII Status: down
MII Polling Interval (ms): 100
Up Delay (ms): 200
Down Delay (ms): 200
**jon@jon-ubuntu:~$** ifconfig
bond0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          UP BROADCAST MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 00:1d:92:97:60:4c
          inet addr:130.215.230.111  Bcast:130.215.231.255  Mask:255.255.254.0
          inet6 addr: fe80::21d:92ff:fe97:604c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1485284 (1.4 MB)  TX bytes:170820 (166.8 KB)
          Base address:0x1400 Memory:e8820000-e8840000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23100 (22.5 KB)  TX bytes:23100 (22.5 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:192.168.2.33  P-t-P:192.168.2.30  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:4180 (4.0 KB)  TX bytes:94 (94.0 B)

```

---

