---
title: "2 Nics and 2 Subnets"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by UbuJack on 2009-06-03
Hi Everyone,

I'm hoping someone can help me here with this infuriating problem. Sure isn't just a lack of knowledge on my part but here you go.

I'm using Ubuntu 8.10 PC to compare folders on 2 Redhat web servers that are on 2 subnets. The Ubuntu PC can successfully connect to anyone of the webservers at any one time (using SSH) but not simultaneously. When I connect it up to both of the subnets at the same time the operating system refuses to access either of them. When I say refuses to access, I cannot ping the subnets default gateway and nslookup's stop working.

The subnets are:

                192.168.30.*
                192.168.31.*

Ifconfig, when I can access one subnet (192.168.30.3):

eth2      Link encap:Ethernet  HWaddr 00:0c:29:bb:fe:ba 
          inet6 addr: fe80::20c:29ff:febb:feba/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:115155 (115.1 KB)  TX bytes:210529 (210.5 KB)
          Interrupt:18 Base address:0x1400

eth3      Link encap:Ethernet  HWaddr 00:0c:29:bb:fe:c4 
          inet addr:192.168.30.3  Bcast:192.168.30.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:febb:fec4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3236527 (3.2 MB)  TX bytes:625597 (625.5 KB)
          Interrupt:19 Base address:0x1480

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1636 (1.6 KB)  TX bytes:1636 (1.6 KB)

Ifconfig, when I cannot access either subnet :

eth2      Link encap:Ethernet  HWaddr 00:0c:29:bb:fe:ba 
          inet addr:192.168.31.3  Bcast:192.168.31.255  Mask:255.255.255.0

          inet6 addr: fe80::20c:29ff:febb:feba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:115275 (115.2 KB)  TX bytes:212333 (212.3 KB)

          Interrupt:18 Base address:0x1400

eth3      Link encap:Ethernet  HWaddr 00:0c:29:bb:fe:c4 
          inet addr:192.168.30.3  Bcast:192.168.30.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:febb:fec4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3590263 (3.5 MB)  TX bytes:744910 (744.9 KB)

          Interrupt:19 Base address:0x1480

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1636 (1.6 KB)  TX bytes:1636 (1.6 KB)

Being able to connect to them simultaneously is pretty important if I'm going to compare these systems without having to copy their entire file structures each time.

Thanks for any help or even reading this

Cheers, Jack

---

### Post by superprash2003 on 2009-06-03
you could NAT them , [http://www.billauer.co.il/ipmasq-html.html](http://www.billauer.co.il/ipmasq-html.html)

---

### Post by UbuJack on 2009-06-03
Thanks for the reply but could you be more specific? 

I don't have much networking knowledge thought I do understand that NAT essentially is a method of presenting a single IP address at one side of the NAT which is shared by multiple IPs on the other side.

I need both NICs to keep their addresses on their LANs/Subnets so I don't see how NAT'ing will help? What am I missing here?

Many thanks

Jack

---

