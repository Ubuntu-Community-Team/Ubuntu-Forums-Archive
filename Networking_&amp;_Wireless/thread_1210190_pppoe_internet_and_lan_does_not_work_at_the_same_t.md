---
title: "pppoe internet and lan does not work at the same time"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by mayacreator on 2009-07-11
Hi, Ubuntu people. I connected to internet by using pppoeconf and simultaneously connected to local network of my provider. Here is my /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```

So, with this settings I automatically connect to internet on computer`s startup, but I can`t connect and browse local network in the same time.
When I change in /etc/network/interfaces that line "iface eth0 inet manual" to something like this "iface eth0 inet dhcp" then I can browse local resources but can`t browse internet. What can I do with it? It`s just making me crazy.
Thanks.

---

### Post by prshah on 2009-07-11
> **mayacreator said:**
> 
```

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
[color=red]pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf[/color]
provider dsl-provider

[color=red]auto eth0
iface eth0 inet manual[/color]

```

So, with this settings I automatically connect to internet on computer`s startup, but I can`t connect and browse local network in the same time.
When I change in /etc/network/interfaces that line "iface eth0 inet manual" to something like this "iface eth0 inet dhcp" then I can browse local resources but can`t browse internet. What can I do with it? It`s just making me crazy.
Thanks.

There's something screwed up here. Is your LAN wire connected to the ADSL modem, or is it connected to the network? According to your posted interfaces file, both are using eth0. 

Some more information please, including network layout (approximate is fine, no need for details), type / make of ADSL modem, etc.

---

### Post by mayacreator on 2009-07-11
I have just cable that connect me to local network, and connection to internet through provider`s router I get my IP using dhcp
Here is what I have executing ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:a4:19:68  
            inet6 addr: fe80::21d:7dff:fea4:1968/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:1361706 errors:0 dropped:0 overruns:0 frame:0
            TX packets:1690615 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:310968986 (310.9 MB)  TX bytes:2237431321 (2.2 GB)
            Interrupt:252 Base address:0xc000 
  
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:86260 errors:0 dropped:0 overruns:0 frame:0
            TX packets:86260 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:13425384 (13.4 MB)  TX bytes:13425384 (13.4 MB)
  
  ppp0      Link encap:Point-to-Point Protocol  
            inet addr:192.168.0.36  P-t-P:10.10.63.1  Mask:255.255.255.255
            UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
            RX packets:865131 errors:0 dropped:0 overruns:0 frame:0
            TX packets:1690031 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:3 
            RX bytes:251752436 (251.7 MB)  TX bytes:2200214728 (2.2 GB)
```
End here is route-n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.63.1      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
```


When I change in /etc/network/interfaces that line "iface eth0 inet manual" to something like this "iface eth0 inet dhcp" then I can browse local resources but can`t browse internet. Here is ifconfig in this case
```

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:a4:19:68  
          inet addr:10.10.0.127  Bcast:10.10.3.255  Mask:255.255.252.0
          inet6 addr: fe80::21d:7dff:fea4:1968/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:498828 (498.8 KB)  TX bytes:13663 (13.6 KB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.0.36  P-t-P:10.10.63.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:52 (52.0 B)  TX bytes:64 (64.0 B)

```
End here is route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.63.1      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.10.0.0       0.0.0.0         255.255.252.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.10.0.1       0.0.0.0         UG    100    0        0 eth0
```

---

### Post by mgblake7 on 2012-04-10
Was this ever solved?

I have the same problem running 10.04

---

