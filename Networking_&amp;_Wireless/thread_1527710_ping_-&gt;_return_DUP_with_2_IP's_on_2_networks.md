---
title: "ping -&gt; return DUP with 2 IP's on 2 networks"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by manuxRhénan on 2010-07-09
Hello,

I use ubuntu 10.04 with 2 network interfaces, dhcpclient on the first interface that connect to internet, dnsmasq for the other for my "private" network, arno iptable for routing/firewall.

When I ping the server from computers on the internal network, here what I get:

```
manu@MyComputer ~ $ ping fitPC
PING fitPC (192.168.10.1): 56 data bytes
64 bytes from 192.168.10.1: icmp_seq=0 ttl=64 time=0.262 ms
64 bytes from 192.168.0.239: icmp_seq=0 ttl=255 time=4.547 ms (DUP!)
64 bytes from 192.168.10.1: icmp_seq=1 ttl=64 time=0.373 ms
64 bytes from 192.168.0.239: icmp_seq=1 ttl=255 time=4.559 ms (DUP!)

```

I don't understand why I get two answers and moreover from 2 Networks...

ifconfig on the server gives:
```
eth0      Link encap:Ethernet  HWaddr 00:01:c0:07:6c:2b  
          inet adr:192.168.10.1  Bcast:192.168.10.255  Masque:255.255.255.0
          adr inet6: fe80::201:c0ff:fe07:6c2b/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:1420780 erreurs:0 :0 overruns:0 frame:0
          TX packets:1641672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1112509118 (1.1 GB) Octets transmis:2080n36639 (2.0 GB)
          Interruption:24 Adresse de base:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:01:c0:07:6c:2c  
          inet adr:192.168.178.35  Bcast:192.168.178.255  Masque:255.255.255.0
          adr inet6: fe80::201:c0ff:fe07:6c2c/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:566369 erreurs:0 :0 overruns:0 frame:0
          TX packets:367970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:766731471 (766.7 MB) Octets transmis:37994581 (37.9 MB)
          Interruption:25 Adresse de base:0x2000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:172 erreurs:0 :0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:14014 (14.0 KB) Octets transmis:14014 (14.0 KB)


```

Isn't that a little bit strange???

---

