---
title: "Can't Connect to internet on ubuntu 11.10 / hp pavillion 1355-dx"
date: 2012-04-17
forum: Networking &amp; Wireless
---

### Post by tab00 on 2012-04-17
Hello there, I recently started having troubles with my networking after I was trying to set up a dns server using bind9 and maradns. Everything was working fine, then when I restarted the computer, I was unable to ssh into the computer or vnc into it. 

When I try ```
ifconfig
``` I get this response:
```

wlan0[CENTER]link encap:Ethernet HWaddr 00:1e:64:80:6f:c4
inet addr:192.168.2.25 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::21e::64ff::fe80::6fc4/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  METRIC:1
RX Packets:919844 errors:0 dropped:0 overruns:0 frame:0
TX Packets:2305 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:203697658 (203.6 MB)   TX bytes:704319 (704.3 KB)[/CENTER]

```

When I try ```
ping google.com
``` this is the response I get:
```

ping: unkown host google.com

```

When I try pinging my router ```
ping -c 4 192.168.2.2
``` I get this:
```

PING 192.168.2.2 (192.168.2.2) 56(84) bytes of data.
From 192.168.2.25 icmp_seq=1 Destination Port Unreachable
From 192.168.2.25 icmp_seq=1 Destination Port Unreachable
From 192.168.2.25 icmp_seq=1 Destination Port Unreachable
From 192.168.2.25 icmp_seq=1 Destination Port Unreachable

--- 192.168.2.2 ping statistics ---
0 packets transmitted, 0 received, +4 errors

```

I tried checking the routing table, and I can't make sense of it.
```

netstat -n

```
returns:
```

Kernel IP routing table
Destination   Gateway     Genmask       Flags Metric Ref  Use Iface
0.0.0.0       192.168.2.2 0.0.0.0       UG    100    0    0   wlan0
169.254.0.0   0.0.0.0     255.255.0.0   U     1000   0    0   wlan0
192.168.2.0   0.0.0.0     255.255.255.0 U     0      0    0   wlan0

```

I really can't figure out why it's doing this. Any help would be much appreciated.
Thanks, Tab00

---

