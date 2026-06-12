---
title: "Virtual Ubuntu Server as router"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by Thalyr on 2013-03-06
Hi,

I'm trying to configure a virtual Ubuntu Server as a router. I think I got all the settings right, but if that were true I wouldn't be posting here..

First, let me explain what I'm trying to do:

I have a Windows PC (a real one, not virtual), it has 1 network interface, IP = 192.168.1.31

I have a virtual Ubuntu Server with 4 interfaces:
eth0: 192.168.1.139
eth1: 192.168.11.139
eth2: 192.168.12.139
eth3: 192.168.13.139

And a virtual CentOS with 4 interfaces:
eth0: 192.168.1.136 (this one is disabled during testing)
eth1: 192.168.11.136
eth2: 192.168.12.136
eth3: 192.168.13.136

Here's a diagram:
```

                           192.168.1.1/24
    +------------+-------------------------------+
    |            |                               |
    |            |                               X
    |            |        192.168.11.0/24         
    |            |     ----------------------    |
   31           139   /   192.168.12.0/24    \  136
 Windows       Ubuntu ------------------------ Centos
                      \   192.168.13.0/24    /
                       ----------------------

```

Both eth0 are connected to my switch and everything on 192.168.1.0/24 is working without problems.
The other interfaces are connected through an internal VMware connection.

Windows can ping Ubuntu, Ubuntu can ping Windows.
Ubuntu can ping all 3 interfaces of Centos and the other way around.
Windows can ping 1 interface from Centos, but not the other 2. Centos cannot ping Windows at all. Traceroute shows that they get to the Ubuntu but not further.

And yes, IP forwarding is on.

Output from Ubuntu:
```

user@UbuntuServer:~$ sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 1

user@UbuntuServer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:56:13:90:00
          inet addr:192.168.1.139  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe13:9000/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:572 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:868318 (868.3 KB)  TX bytes:78458 (78.4 KB)

eth1      Link encap:Ethernet  HWaddr 00:50:56:13:90:01
          inet addr:192.168.11.139  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe13:9001/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27938 (27.9 KB)  TX bytes:14743 (14.7 KB)

eth2      Link encap:Ethernet  HWaddr 00:50:56:13:90:02
          inet addr:192.168.12.139  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe13:9002/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25330 (25.3 KB)  TX bytes:16229 (16.2 KB)

eth3      Link encap:Ethernet  HWaddr 00:50:56:13:90:03
          inet addr:192.168.13.139  Bcast:192.168.13.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe13:9003/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25150 (25.1 KB)  TX bytes:12533 (12.5 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6996 (6.9 KB)  TX bytes:6996 (6.9 KB)

user@UbuntuServer:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.12.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.13.0    0.0.0.0         255.255.255.0   U     0      0        0 eth3


user@UbuntuServer:~$ ping 192.168.1.31 -c 1
PING 192.168.1.31 (192.168.1.31) 56(84) bytes of data.
64 bytes from 192.168.1.31: icmp_req=1 ttl=128 time=0.404 ms

user@UbuntuServer:~$ ping 192.168.11.136 -c 1
PING 192.168.11.136 (192.168.11.136) 56(84) bytes of data.
64 bytes from 192.168.11.136: icmp_req=1 ttl=64 time=0.648 ms

user@UbuntuServer:~$ ping 192.168.12.136 -c 1
PING 192.168.12.136 (192.168.12.136) 56(84) bytes of data.
64 bytes from 192.168.12.136: icmp_req=1 ttl=64 time=5.69 ms

```

Output from Windows:
Note that I can reach all interfaces from the Ubuntu server, even the ones on a different subnet.
```

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.1.1     192.168.1.31     10
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      192.168.1.0    255.255.255.0         On-link      192.168.1.31    266
     192.168.1.31  255.255.255.255         On-link      192.168.1.31    266
    192.168.1.255  255.255.255.255         On-link      192.168.1.31    266
     192.168.10.0    255.255.255.0    192.168.1.139     192.168.1.31     11
     192.168.11.0    255.255.255.0    192.168.1.139     192.168.1.31     11
     192.168.12.0    255.255.255.0    192.168.1.139     192.168.1.31     11
     192.168.13.0    255.255.255.0    192.168.1.139     192.168.1.31     11
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link      192.168.1.31    266
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link      192.168.1.31    266

Pinging 192.168.1.139 with 32 bytes of data:
Reply from 192.168.1.139: bytes=32 time<1ms TTL=64

Pinging 192.168.11.139 with 32 bytes of data:
Reply from 192.168.11.139: bytes=32 time<1ms TTL=64

Pinging 192.168.12.139 with 32 bytes of data:
Reply from 192.168.12.139: bytes=32 time<1ms TTL=64


Pinging 192.168.11.136 with 32 bytes of data:
Reply from 192.168.11.136: bytes=32 time=7ms TTL=63

Pinging 192.168.12.136 with 32 bytes of data:
Request timed out.

Pinging 192.168.13.136 with 32 bytes of data:
Request timed out.

Tracing route to 192.168.12.136 over a maximum of 30 hops
  1    <1 ms    <1 ms    <1 ms  UBUNTUSERVER [192.168.1.139]
  2     *        *        *     Request timed out.
  3     *        *        *     Request timed out.

```

Output from Centos
Note that eth0 is down
```

[root@CentOS ~]# sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 0

[root@CentOS ~]# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:56:13:60:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:70085 (68.4 KiB)  TX bytes:7490 (7.3 KiB)

eth1      Link encap:Ethernet  HWaddr 00:50:56:13:60:01
          inet addr:192.168.11.136  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe13:6001/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:33144 (32.3 KiB)  TX bytes:7017 (6.8 KiB)

eth2      Link encap:Ethernet  HWaddr 00:50:56:13:60:02
          inet addr:192.168.12.136  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe13:6002/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:32419 (31.6 KiB)  TX bytes:4423 (4.3 KiB)

eth3      Link encap:Ethernet  HWaddr 00:50:56:13:60:03
          inet addr:192.168.13.136  Bcast:192.168.13.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe13:6003/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29284 (28.5 KiB)  TX bytes:4453 (4.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

[root@CentOS ~]# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.13.0    0.0.0.0         255.255.255.0   U     0      0        0 eth3
192.168.12.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1003   0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1004   0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1005   0        0 eth3
0.0.0.0         192.168.11.139  0.0.0.0         UG    0      0        0 eth1


[root@CentOS ~]# traceroute 192.168.1.31 -m 5
traceroute to 192.168.1.31 (192.168.1.31), 5 hops max, 60 byte packets
 1  192.168.11.139 (192.168.11.139)  0.578 ms  0.541 ms  0.598 ms
 2  * * *
 3  * * *

```

Sorry for the wall of code, but this has been driving me crazy for some time now. Any help in troubleshooting this would be greatly appreciated.

---

