---
title: "ppp &amp; vpn"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by sourceforge on 2009-04-17
Hi,

I try to up my vpn internet connection. All is fine, but I can't ping anything:
[I]
$ ping google.com
ping: unknown host google.com[/I]

My /etc/ppp/peers/crelcom file:

[I]pty "pptp  10.240.1.1 --nolaunchpppd"
name "xxx"
password "xxx"
usepeerdns
nomppe
noauth
debug
updetach
lock
nobsdcomp
nodeflate
nopcomp
persist
[/I]

Routes before connection:

[I]$ route -n
Kernel IP routing table
Destination Gateway     Genmask       Flags Metric Ref Use Iface
10.240.12.0 0.0.0.0     255.255.255.0 U     0      0   0   eth0
default     10.240.12.1 0.0.0.0       UG    100    0   0   eth0
[/I]

VPN connection:

[I]$ pon crelcom
$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:123.xxx.xxx.xxx  P-t-P:345.xxx.xxx.xxx  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:885 (885.0 B)  TX bytes:70 (70.0 B)
[/I]

Now:

[I]
$ route add default dev ppp0
[/I]

But

[I]
$ ping google.com
ping: unknown host google.com[/I]

Any suggestions?

Thanks.

---

