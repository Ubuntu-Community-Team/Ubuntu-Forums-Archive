---
title: "Help with rtorrent and openvpn (anonine)"
date: 2012-12-11
forum: Networking &amp; Wireless
---

### Post by junkyhlm on 2012-12-11
Hi. I've been googling for some time now and without any clear results. I only want to route the rtorrent traffic through openvpn. From what i can find on the interwebz it is possible but i cant find a clear guide to it.

I'm quite the noob on openvpn but i managed to setup the tunnel. But since i'm also running a webserver on my ubuntu-system i only want the rtorrent traffic to run through openvpn.

Anyone up for teaching a noob some iptables? :)

---

### Post by junkyhlm on 2012-12-12
Anyone?

---

### Post by junkyhlm on 2013-01-08
**What i've tried so far:**
I've tried to setup a VLAN with id 10 on eth0 (eth0.10) with the ip address 10.x.x.x and then added a advanced policy routing to this. This seemed to be working for a while but then it struck me. I dont have a gateway in the new routing table so i weren't able to get out to the internet.
The next problem was that when adding the eth0 gateway (192.168.1.1) to the eth0.10 interface, the two interfaces wasn't able to communicate with each other.

So after consulting a friend he thought that i should put th VLAN on the same subnet so trigger happy i changed the eth0.10 ip to 192.168.1.69 but then i got a error message from RTNETLINK saying that the file already exists and that the interface eth0.10 failed to get up.

So now i'm stuck... again!

---

### Post by junkyhlm on 2013-01-09
**Some clarification:**
```
holmen@filserver:~$ sudo ifup eth0.10
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
RTNETLINK answers: File exists
Failed to bring up eth0.10.
```

**ifconfig:**
```

holmen@filserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:5b:02:5c
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe5b:25c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11670807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22363842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:833725090 (833.7 MB)  TX bytes:31876321312 (31.8 GB)
          Interrupt:44 Base address:0x4000

eth0.10   Link encap:Ethernet  HWaddr 00:1a:4d:5b:02:5c
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe5b:25c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:41501 (41.5 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4899 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:697405 (697.4 KB)  TX bytes:697405 (697.4 KB)
```

```
holmen@filserver:~$ netstat -anr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0.10
```

```
holmen@filserver:~$ ping -I eth0.10 www.dn.se
PING a1910.g1.akamai.net (23.60.69.161) from 192.168.1.2 eth0.10: 56(84) bytes of data.
From filserver.local (192.168.1.69) icmp_seq=1 Destination Host Unreachable
From filserver.local (192.168.1.69) icmp_seq=2 Destination Host Unreachable
From filserver.local (192.168.1.69) icmp_seq=3 Destination Host Unreachable
From filserver.local (192.168.1.69) icmp_seq=4 Destination Host Unreachable
From filserver.local (192.168.1.69) icmp_seq=5 Destination Host Unreachable
From filserver.local (192.168.1.69) icmp_seq=6 Destination Host Unreachable
^C
--- a1910.g1.akamai.net ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6255ms
pipe 3
```

---

