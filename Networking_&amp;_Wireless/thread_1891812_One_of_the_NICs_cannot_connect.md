---
title: "One of the NICs cannot connect"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by tezarin on 2011-12-06
Hi all,
I have an Ubuntu machine which is connected to two switches, IDMZ and ODMZ. The firewall is also connected to the ODMZ switch. Firewall address is 192.168.1.1. This Ubuntu box has two network cards.
The machine can be reached from a 63. address but should be able reachable via a 192. address while inside the firewall. The problem is it can ping yahoo.com just fine but can't ping another machine in the same network or even the default gateway: 192.168.1.1
Here are some outputs:
```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:3c:77:7d
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:35 Base address:0xa000
eth1      Link encap:Ethernet  HWaddr 00:a0:cc:62:34:d5
          inet addr:63.x.x.x  Bcast:63.x.x.x  Mask:255.255.255.128
          inet6 addr: fe80::2a0:ccff:fe62:34d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8024 errors:4 dropped:0 overruns:0 frame:0
          TX packets:436 errors:7 dropped:0 overruns:0 carrier:7
          collisions:0 txqueuelen:1000
          RX bytes:505698 (505.6 KB)  TX bytes:53709 (53.7 KB)
          Interrupt:16 Base address:0xe800
eth2      Link encap:Ethernet  HWaddr 00:14:d1:1e:9a:31
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x2800
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5032 (5.0 KB)  TX bytes:5032 (5.0 KB)
 

```
```

uname -rvo
2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 GNU/Linux
 
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
63.x.x.x     *               255.255.255.128 U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
default         gateway.[half of the domain name here] 0.0.0.0         UG    100    0        0 eth1

```
```

arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.5                         (incomplete)                                   eth0
192.168.1.1                         (incomplete)                                   eth0
63.x.x.x             ether   00:1e:8c:0d:b5:3a   C                      eth1
63.x.x.x              ether   00:0d:48:26:43:76   C                       eth1
 
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
63.x.x.0         0.0.0.0         255.255.255.128 U     0      0        0 eth1
192.168.1.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0           63.x.x.1        0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```
 
If I try to ping outside of the firewall, it works just fine but if I ping a box which is located inside the firewall, it won't work:
```
PING 192.168.1.5 (192.168.1.5) 56(84) bytes of data.
From 192.168.1.13 icmp_seq=1 Destination Host Unreachable
From 192.168.1.13 icmp_seq=2 Destination Host Unreachable
From 192.168.1.13 icmp_seq=3 Destination Host Unreachable

```
 
Can someone please help me figure this out? I would really appreciate it.
 
Thanks,
Tezarin

---

### Post by drdos2006 on 2011-12-06
You need to bond the NICs.
Check these out.

[http://ubuntuforums.org/showthread.php?t=1842656](http://ubuntuforums.org/showthread.php?t=1842656)

[http://ubuntuforums.org/showthread.php?t=1840543](http://ubuntuforums.org/showthread.php?t=1840543)

regards

---

