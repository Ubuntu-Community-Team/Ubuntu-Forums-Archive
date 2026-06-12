---
title: "Ping with VLAN + TOS"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by pakerole on 2012-12-09
Hi all,


I configured my lubuntu to have VLAN 1000 at eth0. And i set this interface to have 802.1p tagging '2'. 


eth0.1000 Link encap:Ethernet  HWaddr 00:26:b9:f3:cb:e4  
          inet addr:192.168.100.2  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fef3:cbe4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1430 (1.4 KB)  TX bytes:1798 (1.7 KB)

The problem is, when i try to ping using this interface  and capture the packet using TCPDUMP, the ping packet sent was not tagged with VLAN priority '2', if "-Q" parameters was set in ping command. 

If i ping without "-Q" No, problem at all. Test methodology as below 

1. fakrul@ubuntu:~$ ping -I eth0.1000 192.168.100.1 -c 1 

tcpdump > 11:36:00.650729 00:26:b9:f3:cb:e4 (oui Unknown) > 00:25:9e:ee:a1:18 (oui Unknown), ethertype 802.1Q (0x8100), length 102: vlan 1000, [COLOR="Red"]p 2[/COLOR], ethertype IPv4, (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84)
    192.168.100.2 > 192.168.100.1: ICMP echo request, id 7240, seq 1, length 64


2. fakrul@ubuntu:~$ ping -I eth0.1000 192.168.100.1 -c 1 -Q 0x48


tcpdump > 11:37:16.800480 00:26:b9:f3:cb:e4 (oui Unknown) > 00:25:9e:ee:a1:18 (oui Unknown), ethertype 802.1Q (0x8100), length 102: vlan 1000, [COLOR="red"]p 0[/COLOR], ethertype IPv4, ([COLOR="red"]tos 0x48[/COLOR], ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84)
    192.168.100.2 > 192.168.100.1: ICMP echo request, id 7244, seq 1, length 64

*when -Q parameters was set, the ping packet sent was tagged with priority '0' instead of '2'

---

### Post by ohnonot on 2012-12-12
2 days without reply.

ubuntu forums probably are not the right place to ask such specialised (and not necesaarily ubuntu specific) questions.

i hope you get some help!

---

