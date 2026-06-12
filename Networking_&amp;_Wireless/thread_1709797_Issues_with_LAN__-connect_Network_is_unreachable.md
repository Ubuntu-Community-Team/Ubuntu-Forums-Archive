---
title: "Issues with LAN  -connect: Network is unreachable"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by Zeppelin! on 2011-03-18
I apologize for the vague title, I cannot think of a descriptive title for this issue.

In brief: I am trying to network two computers together, specifically a WinXP and a Kubuntu machine. The Kubuntu machine is connected physically correctly, ethernet card lights up, the two computers send packets at each other, but Kubuntu doesn't seem to be able to complete the connection. Pinging the WinXP machine results in the cryptic message from the title "connect: Network is unreachable". ping localhost works normally.

Something that worries me:
user$ route -n
Kernel IP routing table
Destination    Gateway       Genmask      Flags Metric Ref   Use Iface
user$

[in /etc/network/interfaces:

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.101

]

Another thing that worries me, someone was trying to help me resolve this before they had to depart, and I got this from the command they gave.
user$ sudo route add default gw 192.168.1.101 eth0
[sudo]
SIOCADDRT: No such process
user$

Interestingly, the ifup for eth0 has already been completed.

I really am at a loss for how to proceed.

Edit-to-Add:
ifconfig
eth0
Link encap:Ethernet  HWaddr 00:16:76:b2:8a:7d
inet6 addr:  fe80::216:76ff:feb2:8a7d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX packets:214 errors:0 dropped:0 overruns:0 frame:0
TX packets:29 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txquelen:1000
RX bytes: 25506 (25.5 KB)  TX bytes:6924 (6.9 KB)
Interrupt:21 Base address:0x1000

---

