---
title: "Destination suddenly not reachable"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by lkytmr on 2011-02-14
I have been running mediawiki on an ubuntu machine for six months on IP 172.26.3.223.

The wiki stopped responding one day in the middle of a wiki page edit and I found that I could no longer ping 172.26.3.223 from Windows.  I found that if I set the machine’s IP to 172.26.3.224, it works. Any other IP except for .223 works. 

My interface file and output from ifconfig are included below.

I have three IP addresses on this one machine, 

1.)	one assigned from DHCP (usually 172.26.3.137),
2.)	one static IP 172.26.3.223 (this is the one that stopped working)
3.)	one static IP 172.26.3.225 (this one still works)

My window’s machines 

1.)	Cannot ping 172.26.3.137 (Destination host unreachable.)
2.)	Cannot ping 172.26.3.223 (Destination host unreachable.)
3.)	Can ping 172.26.3.225

My ubuntu-mediawiki machine 

1.)	Can ping all three of its own IP addresses
2.)	Can ping external IP addresses

Thanks for any help you can offer
Tom 

Here is my interfaces file:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth0:1
iface eth0:1 inet static
address 172.26.3.225
netmask 255.255.0.0
gateway 172.26.0.1

auto eth0:2
iface eth0:2 inet static
address 172.26.3.223
netmask 255.255.0.0


Here is the output of ifconfig
Last login: Mon Feb 14 09:33:05 2011 from 172.26.3.119
tmr@csc-wiki:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:87:b5:fc
          inet addr:172.26.3.137  Bcast:172.26.255.255  Mask:255.255.0.0
          inet6 addr: fe80::2e0:4cff:fe87:b5fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18092 (18.0 KB)  TX bytes:24571 (24.5 KB)
          Interrupt:22 Base address:0xe800

eth0:1    Link encap:Ethernet  HWaddr 00:e0:4c:87:b5:fc
          inet addr:172.26.3.225  Bcast:172.26.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xe800

eth0:2    Link encap:Ethernet  HWaddr 00:e0:4c:87:b5:fc
          inet addr:172.26.3.223  Bcast:172.26.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1248 (1.2 KB)  TX bytes:1248 (1.2 KB)

---

### Post by Iowan on 2011-02-14
Probably won't shed any new light, but...
What's in your routing table (**route -n**)?

---

### Post by lkytmr on 2011-02-15
As it turns out, our IT guy shut my wiki down. I'm not sure how you go about turning an IP address off but I'm assuming the gateway has a table that you can blacklist ip addresses with.

Its really irritating because he turned it off and never said a word. Cost me a days worth of work.

He's a control freak.

---

