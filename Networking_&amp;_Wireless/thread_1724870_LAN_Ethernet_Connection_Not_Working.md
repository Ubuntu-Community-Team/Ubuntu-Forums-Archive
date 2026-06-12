---
title: "LAN Ethernet Connection Not Working"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by gazza_11 on 2011-04-08
Hi,

(Ubuntu 9.10)

My three-PC LAN has a star topology; a 'main' computer has two Ethernet cards (unbridged) in it which directly connect it to two 'remote' machines.  The problem is that I can only communicate on one of the two subnets.  Pinging on the other subnet returns a 'Destination Host Unreachable' error.  I tested the hardware by having each card fitted on its own in turn, first with its usual IP address then with the IP address normally of the other card and everything worked.  But with both cards installed, only one subnet works.  Furthermore, it's not a particular IP address issue; 192.168.1.1 connected to 192.168.1.2 _and_ 192.168.2.1 connected to 192.168.2.2 _both_ work -- but not together.  There is also, by the way, an Internet connection using a USB broadband dongle (mobile phone network).  Here's the output of 'ifconfig':

```
eth0      Link encap:Ethernet  HWaddr 00:50:bf:93:6a:94  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe93:6a94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0x8400 

eth2      Link encap:Ethernet  HWaddr 00:50:bf:93:6a:9a  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe93:6a9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100946 (100.9 KB)  TX bytes:76797 (76.7 KB)
          Interrupt:5 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3958250 (3.9 MB)  TX bytes:3958250 (3.9 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:178.97.230.189  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3358477 (3.3 MB)  TX bytes:291965 (291.9 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```Here's the output of 'route':

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
192.168.2.0     *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth2
default         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0

```

What could be up?

gazza_11.

---

