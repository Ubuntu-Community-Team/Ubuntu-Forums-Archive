---
title: "Wired connection doesn’t work..."
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by Hvidemose on 2013-07-10
[FONT=Verdana][SIZE=2]Using[/SIZE][/FONT][FONT=Verdana][SIZE=2] Ubuntu 13.04. [/SIZE][/FONT][FONT=Verdana][SIZE=2]My [/SIZE][/FONT][FONT=Verdana][SIZE=2]wifi functions well, but I can't get any data through my Ethernet connection. It acknowledge that the cable is in, [/SIZE][/FONT][FONT=Verdana][SIZE=2]and sometimes it works for a minute, [/SIZE][/FONT][FONT=Verdana][SIZE=2]but [/SIZE][/FONT][FONT=Verdana][SIZE=2]after that there is[/SIZE][/FONT][FONT=Verdana][SIZE=2] no connection...



Does any one have the same problem, or can someone help me to get the Ethernet connection up and running?


Cheers! [/SIZE][/FONT]

---

### Post by KeepItSimpleStupid on 2013-07-10
I was expecting somewhat of a more seemless connection.  I'm running the LIVE CD only. I ave good luck sonnecting to wireless if I go to the Network control panel first.  Make sure wireless is OFF when using using wireless.

Using:
ubuntu@ubuntu:/$ ping -s 8192 10.0.1.1
PING 10.0.1.1 (10.0.1.1) 8192(8220) bytes of data.
8200 bytes from 10.0.1.1: icmp_req=1 ttl=64 time=74.8 ms
8200 bytes from 10.0.1.1: icmp_req=2 ttl=64 time=72.7 ms
8200 bytes from 10.0.1.1: icmp_req=3 ttl=64 time=70.9 ms
8200 bytes from 10.0.1.1: icmp_req=4 ttl=64 time=69.9 ms
8200 bytes from 10.0.1.1: icmp_req=5 ttl=64 time=68.8 ms
8200 bytes from 10.0.1.1: icmp_req=6 ttl=64 time=67.8 ms
8200 bytes from 10.0.1.1: icmp_req=7 ttl=64 time=66.7 ms
8200 bytes from 10.0.1.1: icmp_req=8 ttl=64 time=64.8 ms

pings to your router, where 10.0.1.1 is the address of your router with a large packet size is an easy way to check for gross cable problems.

---

