---
title: "eth1 has no ip"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by nothign on 2011-03-21
I have a freshly installed Ubuntu 10.10... 

It appears as though my eth1 (a built in network card) has no ip.. 

the results of ifconfig are  (hand typed.. so sorry for errors)

```
eth1
Link encap:Ethernet HWaddr 00:13:d4:c3:8d:2e
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1:avahi
Link encap:Ethernet HWaddr 00:13:d4:c3:8d:2e
inet addr:169.254.8.31 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1

lo
Link Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:76088 (76.0 B)  TX bytes:76088 (76.0 B)

```

The contents of /etc/network/interfaces is 

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
address 192.168.1.111
netmask 255.255.255.0
gateway 192.168.1.254
```

and the result of sudo dhclient eth1 is 

```
There is already a pid file /var/run/dhclient.pid with pid 1796
killed old client process, removed PID file
Internet Systems Consortium DHCP Client v3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://ww.isc.org/software/dhcp/

Listeing on LPF/eth1/00:13:d4:c3:8d:2e
Sending on  LPF/eth1/00:13:d4:c3:8d:2e
Sending on  Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Can anybody help?

---

### Post by conneco on 2011-03-21
Youve got your /etc/network/interfaces

set to dhcp and then your trying to static assign it on the next line change
iface eth1 inet dhcp
to
iface eth1 inet static

---

### Post by nothign on 2011-03-21
> **conneco said:**
> Youve got your /etc/network/interfaces

set to dhcp and then your trying to static assign it on the next line change
iface eth1 inet dhcp
to
iface eth1 inet static

I made that change... 

now the contents of ifconfig have the addition of 

```
inet addr:192.168.1.111 Bcast:192.168.1.255 Mask:255.255.255.0
```

under the eth1

But I have no connection still.. Even after restarting the computer and the router.

What else can I do ?

---

