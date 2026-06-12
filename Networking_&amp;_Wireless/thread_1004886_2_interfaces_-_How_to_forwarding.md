---
title: "2 interfaces - How to forwarding?"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by sou1980 on 2008-12-07
Hi all.

I am a linux networking newbie. I have a machine running the latest version of Ubuntu server (32 bit). It has 2 ethernet interfaces:

eth0: 192.168.200.0/24
eth1: 192.168.1.0/24

I have set up OpenVPN in bridge mode, bridging the tap0 interface with eth0. I have configured my ISP router's DHCP server and it works just fine.

What I was trying to do is to make the machines from the 192.168.200.0 subnet "see" the machines of the 192.168.1.0 subnet. In other words, set up a simple router.

How can I do it? I have been reading about iptables but I have got lost. Can you help me?

Thank you,
Stavros

PS: Here is the output of ifconfig -a

br0       Link encap:Ethernet  HWaddr 00:30:1b:46:ae:13
          inet addr:192.168.200.101  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:fe46:ae13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1857953 (1.7 MB)  TX bytes:828008 (808.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:30:1b:46:ae:13
          inet6 addr: fe80::230:1bff:fe46:ae13/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:5399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2012572 (1.9 MB)  TX bytes:888458 (867.6 KB)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:19:e0:10:75:57
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e0ff:fe10:7557/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15809 (15.4 KB)  TX bytes:24587 (24.0 KB)
          Interrupt:20 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:264 (264.0 B)  TX bytes:264 (264.0 B)

tap0      Link encap:Ethernet  HWaddr 00:ff:02:0e:f4:41
          inet6 addr: fe80::2ff:2ff:fe0e:f441/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3434 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:91199 (89.0 KB)  TX bytes:965333 (942.7 KB)

---

### Post by Iowan on 2008-12-08
You've probably seen [this]("https://help.ubuntu.com/community/IptablesHowTo") Help page.  I also found this router [How-To]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html").

---

