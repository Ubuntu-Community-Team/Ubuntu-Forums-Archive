---
title: "*** need Help *** - Getting more than one public IP from my cablemodem."
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by stachendrath on 2008-12-08
Hi all , this is my first post. My name is Leonard from Argentina and i need help. First i ll decribe my idea ,then what i tried.


I have a Dev Server ( os: ubuntu )for my test with one nic. A cablemodem Coax Conection with 10 Public IPs. my problem is that i  dont have 10 nics to ask for the 10 ips :D . so my idea is to creat tunnels ( or virtual interfaces ) to get those 10 publics ips.

But i have a problem . i dont know how to implement this solution.
The IPs must be asked via DHCP to my cablemodem.

I follow this tutorial 

Emulating multiple nics with one
[http://linux.derkeiler.com/pdf/Newsgroups/comp.os.linux.networking/2007-11/msg00139.pdf](http://linux.derkeiler.com/pdf/Newsgroups/comp.os.linux.networking/2007-11/msg00139.pdf).

But the taps ( tap1 and tap2 ) dont get ips from DHCP.
any idea ? if someone have an idea  , please help me ,and if u need more information just ask me.

here is my ifconfig 

#####################################################33

root@devsrv1:~# ifconfig
br0       Link encap:Ethernet  HWaddr 00:06:4f:5d:ce:45
          inet addr:190.189.104.xx ( Public IP )  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe5d:ce45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101187747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:382013070 (364.3 MB)  TX bytes:1334943 (1.2 MB)


eth3      Link encap:Ethernet  HWaddr 00:06:4f:5d:ce:45 ( interfase conected to my modem )
          inet6 addr: fe80::206:4fff:fe5d:ce45/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:103666384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27331381 errors:0 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000
          RX bytes:1957207207 (1.8 GB)  TX bytes:1644444141 (1.5 GB)
          Interrupt:5 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1036549 (1012.2 KB)  TX bytes:1036549 (1012.2 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:6c:a9:9c:11 ( Tap0 is the Hud )
          inet6 addr: fe80::2ff:6cff:fea9:9c11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101101641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:2026260 (1.9 MB)  TX bytes:1771334738 (1.6 GB)

tap1      Link encap:Ethernet  HWaddr 00:ff:4f:4d:f1:23 ( tap1 is not asking for DHCP . i would like to have if from 190.189.x.x )
          inet6 addr: fe80::2ff:4fff:fe4d:f123/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101101647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:1771335206 (1.6 GB)  TX bytes:2025792 (1.9 MB)

tap2      Link encap:Ethernet  HWaddr 00:ff:e3:31:41:03 ( tap0 is not asking for DHCP . i would like to have if from 190.189.x.x )
          inet6 addr: fe80::2ff:e3ff:fe31:4103/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101107569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:1773360530 (1.6 GB)  TX bytes:468 (468.0 B)

############################################################
Here is my br0 config

root@devsrv1:~# brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.00064f5dce45       no              eth3
                                                        tap0
root@devsrv1:~#
 
############################################################

Thanks in Advance
and sorry for my english.

Leonard.

---

### Post by Bruce M. on 2009-01-07
> **stachendrath said:**
> Hi all , this is my first post. My name is Leonard from Argentina and i need help. First i ll decribe my idea ,then what i tried.

Hi Leonard

I live in Bs As as well. I started using a cablemodem with MultiCanal (Flash). It is all one now (Fibertel) and that is when I noticed problems.

I have a Motorola Cablemodem connected to my eth0 card (no router, unless it is built inti the modem). A simple setup.

I'm not sure what you are talking about here with "taps" but I have a problem that might be related.

> **stachendrath said:**
> But the taps ( tap1 and tap2 ) dont get ips from DHCP.
any idea ? if someone have an idea  , please help me ,and if u need more information just ask me.

Thanks in Advance
and sorry for my english.

Leonard.

Your English is better than my Spanish.

I'm running Xubuntu 8.10-64 bit and I deleted NetworkManager according to this: [Howto: Ethernet connection without a GUI]("http://cafelinux.org/xubuntuforums/index.php?PHPSESSID=7244a5f850b6461ab69b04d067267180&topic=145.0") and started configuring things manually. Why, because Fibertel is sending 4 nameservers to my /etc/resolv.config file, that has a "limit" of 3:
```
nameserver 200.xx.xxx.xx
nameserver 200.xx.xxx.xx
nameserver 200.xx.xxx.xx
nameserver 172.xx.x.xx
```
The last one is Fibertels DHCP server and is not being read by Linux.

Check out this thread as well, for Xubuntu: [Are you having problems with Network Manager?]("http://cafelinux.org/xubuntuforums/index.php?topic=143.0").

So, I'm not sure if this is related with the problem you have but if it is maybe we can work this out together.

Have a nice day.
Bruce

---

