---
title: "Can`t access internet with Dlink wbr-2310"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by ramon1093 on 2009-05-08
I bought a Dlink wbr-2310 wireless router, in WinXP everything works OK but when I boot Ubuntu (dual boot in this machine) or PClinuxOS 2009 in my other box both show connection to the network but when I start Firefox it won`t access the internet.


Main box:

Intel P4 3.2ghz
2 GB DDR RAM
Gigabyte 8IPE1000P-G Motherboard
2 - 80GB Maxtor HD
ATI Radeon 9600 256MB
Trendnet TEW-424UB wifi usb
Dual boot winxp - Ubuntu 9.04 fresh install

---

### Post by superprash2003 on 2009-05-09
post output of **ifconfig** from the terminal. wired or wireless?

---

### Post by ramon1093 on 2009-05-10
Here is:

ramon@ramon-ubuntu788:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:61:78:f4:66  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2167 (2.1 KB)  TX bytes:2167 (2.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:57:7a:a1  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe57:7aa1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6926971 (6.9 MB)  TX bytes:565465 (565.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-D1-57-7A-A1-61-61-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I used to have another wireless router and everything was ok, problems started when I bought this new one. I did the fresh install with this new router.

---

### Post by superprash2003 on 2009-05-11
you seem to be getting an ip address on wlan0. post output of **ping 209.85.171.100** and ping **192.168.0.1**

presuming 192.168.0.1 is your router ip..

---

### Post by ramon1093 on 2009-05-12
Here it is, hope this help :

ramon@ramon-ubuntu788:~$ ping 209.85.171.100
PING 209.85.171.100 (209.85.171.100) 56(84) bytes of data.
64 bytes from 209.85.171.100: icmp_seq=1 ttl=228 time=395 ms
64 bytes from 209.85.171.100: icmp_seq=2 ttl=228 time=371 ms
64 bytes from 209.85.171.100: icmp_seq=3 ttl=228 time=356 ms
64 bytes from 209.85.171.100: icmp_seq=4 ttl=228 time=371 ms
64 bytes from 209.85.171.100: icmp_seq=5 ttl=228 time=395 ms
64 bytes from 209.85.171.100: icmp_seq=7 ttl=228 time=299 ms
64 bytes from 209.85.171.100: icmp_seq=9 ttl=228 time=414 ms
64 bytes from 209.85.171.100: icmp_seq=10 ttl=228 time=357 ms


ramon@ramon-ubuntu788:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=5.07 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=5.63 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=5.64 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=4.13 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=127 time=4.76 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=127 time=7.39 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=127 time=5.25 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=127 time=8.14 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=127 time=5.40 ms

I think it is the router because when I reset it start working for a few minutes then stop again.

---

