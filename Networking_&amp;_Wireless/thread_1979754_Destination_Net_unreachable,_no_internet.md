---
title: "Destination Net unreachable, no internet"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by russ15 on 2012-05-14
Hi Everyone,
 
My desktop ubuntu 11.10 has recently started not connecting to the internet; it is a wired connection. The network manager states:
 
Wired network connection 'wired connection 1' active
 
However the internet times out and ping gives 'Destination Net Unreachable'
 
I initially thought that it could be due to a recent upgrade of memory, however the internet has worked since and replacing the old RAM has no effect.
 
It wasn't working last week but when I started up this morning the internet was working fine. I then had to do a restart and the problem is occuring again.
 
The network cable works fine in my laptop.
 
Here are some of the stats any help would be greatly appreciated:
 
&#12288; 
~$ ping 8.8.8.8 
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 
From 10.1.1.1 icmp_seq=1 Destination Net Unreachable 
From 10.1.1.1 icmp_seq=2 Destination Net Unreachable 
From 10.1.1.1 icmp_seq=3 Destination Net Unreachable 
From 10.1.1.1 icmp_seq=4 Destination Net Unreachable 
^C 
--- 8.8.8.8 ping statistics --- 
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3000ms 
 
&#12288;
&#12288;
[FONT=Liberation Serif]~$ ifconfig [/FONT]
[FONT=Liberation Serif]eth0 Link encap:Ethernet HWaddr 38:60:77:29:d6:e6 [/FONT]
[FONT=Liberation Serif]inet addr:10.1.1.5 Bcast:10.255.255.255 Mask:255.0.0.0 [/FONT]
[FONT=Liberation Serif]inet6 addr: fe80::3a60:77ff:fe29:d6e6/64 Scope:Link [/FONT]
[FONT=Liberation Serif]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 [/FONT]
[FONT=Liberation Serif]RX packets:3587 errors:0 dropped:0 overruns:0 frame:0 [/FONT]
[FONT=Liberation Serif]TX packets:248 errors:0 dropped:0 overruns:0 carrier:0 [/FONT]
[FONT=Liberation Serif]collisions:0 txqueuelen:1000 [/FONT]
[FONT=Liberation Serif]RX bytes:460662 (460.6 KB) TX bytes:32626 (32.6 KB) [/FONT]
[FONT=Liberation Serif]Interrupt:20 Memory:fe500000-fe520000 [/FONT]
[FONT=Liberation Serif]lo Link encap:Local Loopback [/FONT]
[FONT=Liberation Serif]inet addr:127.0.0.1 Mask:255.0.0.0 [/FONT]
[FONT=Liberation Serif]inet6 addr: ::1/128 Scope:Host [/FONT]
[FONT=Liberation Serif]UP LOOPBACK RUNNING MTU:16436 Metric:1 [/FONT]
[FONT=Liberation Serif]RX packets:6 errors:0 dropped:0 overruns:0 frame:0 [/FONT]
[FONT=Liberation Serif]TX packets:6 errors:0 dropped:0 overruns:0 carrier:0 [/FONT]
[FONT=Liberation Serif]collisions:0 txqueuelen:0 [/FONT]
[FONT=Liberation Serif]RX bytes:340 (340.0 B) TX bytes:340 (340.0 B)[/FONT]
 
 
 
[FONT=Liberation Serif]~$ netstat -r [/FONT]
[FONT=Liberation Serif]Kernel IP routing table [/FONT]
[FONT=Liberation Serif]Destination Gateway Genmask Flags MSS Window irtt Iface [/FONT]
[FONT=Liberation Serif]default mygateway1.ar7 0.0.0.0 UG 0 0 0 eth0 [/FONT]
[FONT=Liberation Serif]10.0.0.0 * 255.0.0.0 U 0 0 0 eth0 [/FONT]
[FONT=Liberation Serif]link-local * 255.255.0.0 U 0 0 0 eth0 [/FONT]

---

### Post by russ15 on 2012-05-14
A cheap network card has done the trick.

---

