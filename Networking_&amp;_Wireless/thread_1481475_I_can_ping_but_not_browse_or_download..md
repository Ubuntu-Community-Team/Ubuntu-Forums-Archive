---
title: "I can ping but not browse or download."
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by heviejob on 2010-05-12
I have a ubuntu server 9.04 used to authenticate hotspot users and is connected to a mikrotik router.
I can ping and traceroute domains but i cannot browse or download anything. Dns is resolving fine. What may be the issue?

---

### Post by heviejob on 2010-05-12
I forgot to mention that comps on the same subnet can browse and download.

---

### Post by doas777 on 2010-05-12
so you could ping and nslookup [www.google.com](www.google.com), but you can't find it in your browser?

do you have any proxy setting configured on the clients, or their browsers?

---

### Post by heviejob on 2010-05-12
I have no proxies set up on the network. It was working fine before but stopped. The browser resolves domains fine.nslookup works.
 $ nslookup gmail.com
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	gmail.com
Address: 209.85.227.83
Name:	gmail.com
Address: 209.85.227.17
Name:	gmail.com
Address: 209.85.227.18
Name:	gmail.com
Address: 209.85.227.19

I have looked at the gateway and routes but not working.
I have masquerading enabled on the router for subnet 192.168.1.0/24 and router ip is 192.168.1.1 and its the gateway. Could it be an issue with routing?

---

### Post by doas777 on 2010-05-12
> **heviejob said:**
> I have no proxies set up on the network. It was working fine before but stopped. The browser resolves domains fine.nslookup works.
 $ nslookup gmail.com
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    gmail.com
Address: 209.85.227.83
Name:    gmail.com
Address: 209.85.227.17
Name:    gmail.com
Address: 209.85.227.18
Name:    gmail.com
Address: 209.85.227.19

I have looked at the gateway and routes but not working.
I have masquerading enabled on the router for subnet 192.168.1.0/24 and router ip is 192.168.1.1 and its the gateway. Could it be an issue with routing?

it can definetly be a routing issue, if you do not have a default route, or the route is malformed.

what is the output of 
```

sudo ifconfig
sudo route

```

---

### Post by heviejob on 2010-05-12
$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:be:eb:2f  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:a1:b0:20:93:98  
          inet addr:192.168.1.159  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a1:b0ff:fe20:9398/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114276 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:21187982 (21.1 MB)  TX bytes:13399238 (13.3 MB)
          Interrupt:16 Memory:fc510000-fc5100ff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2192 (2.1 KB)  TX bytes:2192 (2.1 KB)

and 

sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1

---

### Post by heviejob on 2010-05-12
when i fetch gmail i get

wget gmail.com
--2010-05-13 00:21:11--  [http://gmail.com/](http://gmail.com/)
Resolving gmail.com... 209.85.227.17, 209.85.227.83, 209.85.227.18, ...
Connecting to gmail.com|209.85.227.17|:80... failed: Connection timed out.
Connecting to gmail.com|209.85.227.83|:80..

---

### Post by heviejob on 2010-05-12
I also have the same issue! what could be the problem?

---

### Post by Iowan on 2010-05-12
Moved #8 to this thread from [here]("http://ubuntuforums.org/showthread.php?t=1373462").> Please do not cross post, or post the same thing in multiple locations.Confuses people - me in particular ;)

I presume you already tried checking MTU? Sometimes disabling IPv6 helps.

---

### Post by jedan83 on 2011-07-16
I have a ubuntu server 11.04 used to authenticate hotspot users and is connected to a mikrotik router. I can ping and traceroute domains but i cannot browse or download anything. Dns is resolving fine. What may be the issue? tanks

---

