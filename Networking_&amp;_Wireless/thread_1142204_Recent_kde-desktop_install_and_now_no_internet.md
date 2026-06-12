---
title: "Recent kde-desktop install and now no internet"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by jfernand on 2009-04-29
I have a weird problem and I feel like I'm spinning my wheels.  I am running 8.04 and I recently installed kde to live along side gnome but now i can't connect to the internet. The weird thing is that I can launch a VM and it can connect to the internet just fine.  I can even SSH into this box (not the VM) from a windows machine. I just can't make any outgoing connections like apt-get or firefox, but...i can ping.

Do you guys/gals have any advice or suggestions?

> [FONT="Courier New"]jfernand@nebula:/etc$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.197.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.248.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

jfernand@nebula:/etc$ ping -c3 74.125.45.100
PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.
64 bytes from 74.125.45.100: icmp_seq=1 ttl=244 time=43.5 ms
64 bytes from 74.125.45.100: icmp_seq=2 ttl=244 time=38.3 ms
64 bytes from 74.125.45.100: icmp_seq=3 ttl=244 time=37.9 ms

--- 74.125.45.100 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 37.937/39.940/43.520/2.542 ms

jfernand@nebula:/etc$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:4b:05:44:10
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:4bff:fe05:4410/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6703969 (6.3 MB)  TX bytes:909840 (888.5 KB)
          Interrupt:222 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:04:4b:05:44:11
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:173528 (169.4 KB)  TX bytes:173528 (169.4 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:192.168.197.1  Bcast:192.168.197.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:172.16.248.1  Bcast:172.16.248.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/FONT]


---

### Post by jfernand on 2009-04-29
Man i feel stupid.  The install apparently cleared my DNS entries and therefore couldn't resolve any addresses. So that explains why ping worked but apt-get didn't work because it couldn't resolve the repositories.

:oops:

---

