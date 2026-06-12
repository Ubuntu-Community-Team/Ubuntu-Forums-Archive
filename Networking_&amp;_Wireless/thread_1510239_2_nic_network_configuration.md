---
title: "2 nic network configuration"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by maclp on 2010-06-15
hi,

im running a server using ubuntu 8.04 and 2 nic's in it.
i'm running dansguardian on it so that all the unwanted internet traffic can be blocked.
i want the LAN part to run on eth0 and the internet on eth1 but i don't know how.
i'd really [I]appreciate help on this.

[/I]> 
administrator@dansguardian1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:75:93:af:cb
          inet addr:26.10.0.160  Bcast:26.10.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:75ff:fe93:afcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:308646 errors:0 dropped:0 overruns:1 frame:0
          TX packets:34012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:75525335 (72.0 MB)  TX bytes:9136790 (8.7 MB)
          Interrupt:19 Base address:0x2c00

eth1      Link encap:Ethernet  HWaddr 00:07:e9:ba:4e:97
          inet addr:26.10.0.161  Bcast:26.10.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6252 (6.1 KB)  TX bytes:6252 (6.1 KB)

administrator@dansguardian1:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
26.10.0.0       *               255.255.255.0         U      0       0        0   eth0
26.10.0.0       *               255.255.255.0         U      0       0        0   eth1
default         speedtouch.lan  0.0.0.0              UG    100    0        0   eth1
default         speedtouch.lan  0.0.0.0              UG    100    0        0   eth0



---

### Post by Iowan on 2010-06-15
Sounds a little like [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing"). There might also be some useful information in the [Server guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html").

---

