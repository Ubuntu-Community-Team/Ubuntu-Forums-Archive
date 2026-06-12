---
title: "Server can't see out."
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by Mesatchornug on 2009-08-17
Short version:

I have a server running Hardy in my apartment. I just moved, and upon setting it up at my new place I'm having some troubles. While the server [[http://www.aarongrossman.com/](http://www.aarongrossman.com/)] is accessible from the outside, I can't access the web from it.

Longer:
I have a linksys router acting as a bridge per the tutorial here:
[http://forums.anandtech.com/messageview.aspx?catid=36&threadid=1513386](http://forums.anandtech.com/messageview.aspx?catid=36&threadid=1513386)

Up to now things have been fine. After the move, the server can't see past the Linksys. In case it merits note, my old apartment was served by Comcast; the new one is Verizon.

When I telnet to the Linksys, it has no problems pinging anything I want. Meanwhile the server can only ping the router and other machines behind it, including itself. At the same time, we can see the server from the outside. IIRC, when my laptop was connected to the Linksys is could see out fine, I'll have to check that when I get home though.

Is this a simple configuration mistake that I'm missing?

---

### Post by superprash2003 on 2009-08-17
post output of** sudo iptables -L** have you tried playing with iptables lately?

---

### Post by Iowan on 2009-08-17
Is the server set with static IP? you may need to update DNS server... or opt  for static lease.

---

### Post by Mesatchornug on 2009-08-17
> **superprash2003 said:**
> post output of** sudo iptables -L** have you tried playing with iptables lately?

Forgive me, I don't know if there's a standard for quoting shell output here, so I'll wrap it as a code block.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

To answer you, I haven't played with iptables at least since I first set up the server ~1.5 years ago, if ever.

---

### Post by Mesatchornug on 2009-08-17
> **Iowan said:**
> Is the server set with static IP? you may need to update DNS server... or opt  for static lease.

It requests a static IP from the Linksys router/bridge, that way I can forward http/ssh/mail/etc traffic to it.

This may be a foolish question - is there an easy way to forward traffic based on MAC rather than IP?

---

### Post by Mesatchornug on 2009-08-17
> **superprash2003 said:**
> post output of** sudo iptables -L** have you tried playing with iptables lately?

output from the router:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere            tcp dpt:webcache 
DROP       tcp  --  anywhere             anywhere            tcp dpt:www 
DROP       tcp  --  anywhere             anywhere            tcp dpt:https 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh 
DROP       tcp  --  anywhere             anywhere            tcp dpt:telnet 
DROP       tcp  --  anywhere             anywhere            tcp dpt:69 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
logdrop    all  --  anywhere             anywhere            state INVALID 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1461:65535 TCPMSS set 1460 
lan2wan    all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 udp 
ACCEPT     tcp  --  anywhere             192.168.1.140       tcp dpt:www 
ACCEPT     udp  --  anywhere             192.168.1.140       udp dpt:www 
ACCEPT     tcp  --  anywhere             192.168.1.140       tcp dpt:smtp 
ACCEPT     udp  --  anywhere             192.168.1.140       udp dpt:25 
ACCEPT     tcp  --  anywhere             192.168.1.140       tcp dpt:pop3 
ACCEPT     udp  --  anywhere             192.168.1.140       udp dpt:pop3 
ACCEPT     tcp  --  anywhere             192.168.1.140       tcp dpt:qotd 
ACCEPT     udp  --  anywhere             192.168.1.140       udp dpt:17 
DROP       tcp  --  192.168.1.140        anywhere            tcp spt:10000 
DROP       udp  --  anywhere             192.168.1.140       udp dpt:10000 
ACCEPT     tcp  --  anywhere             192.168.1.142       tcp dpt:5900 
ACCEPT     udp  --  anywhere             192.168.1.142       udp dpt:5900 
ACCEPT     tcp  --  anywhere             192.168.1.140       tcp dpt:https 
ACCEPT     udp  --  anywhere             192.168.1.140       udp dpt:https 

```

If it helps, these posts were made from my laptop, attached to the same router.
output for this laptop:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      
```

---

### Post by superprash2003 on 2009-08-18
it could be your router , blocking certain traffic.. do try checking its settings.. also post output of **route -n**

---

### Post by Mesatchornug on 2009-08-18
> **superprash2003 said:**
> also post output of **route -n**

per the router:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.128   0.0.0.0         255.255.255.128 U     0      0        0 br0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth2

```per my server:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.129   0.0.0.0         UG    100    0        0 eth0


```

---

### Post by superprash2003 on 2009-08-19
could you post output of ifconfig from the terminal , whats your router's ip address?

---

### Post by Mesatchornug on 2009-08-19
> **superprash2003 said:**
> could you post output of ifconfig from the terminal , whats your router's ip address?

from the server:
```

eth0      Link encap:Ethernet  HWaddr 00:07:e9:01:a9:3f
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe01:a93f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29929 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2474289 (2.3 MB)  TX bytes:6230661 (5.9 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1460941 (1.3 MB)  TX bytes:1460941 (1.3 MB)

```from the linksys:
```

br0       Link encap:Ethernet  HWaddr 00:0C:41:9C:B6:87
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.128
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:47657099 (45.4 MiB)  TX bytes:75338115 (71.8 MiB)

eth0      Link encap:Ethernet  HWaddr 00:0C:41:9C:B6:87
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154109 errors:3 dropped:0 overruns:3 frame:3
          TX packets:390859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:51674804 (49.2 MiB)  TX bytes:94540935 (90.1 MiB)
          Interrupt:3 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:0C:41:9C:B6:88
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:80730 (78.8 KiB)
          Interrupt:4 Base address:0x8000

eth2      Link encap:Ethernet  HWaddr 00:0C:41:9C:B6:88
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127116 errors:0 dropped:0 overruns:0 frame:6768203
          TX packets:119982 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:74452029 (71.0 MiB)  TX bytes:45815083 (43.6 MiB)
          Interrupt:6 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING MULTICAST  MTU:16436  Metric:1
          RX packets:470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:33824 (33.0 KiB)  TX bytes:33824 (33.0 KiB)

vlan0     Link encap:Ethernet  HWaddr 00:0C:41:9C:B6:87
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:390859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:48900792 (46.6 MiB)  TX bytes:94540935 (90.1 MiB)

vlan1     Link encap:Ethernet  HWaddr 00:0C:41:9C:B6:87
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

if you mean internally, the server is 192.168.1.140, the Linksys is *.129, and the primary router is *.1
from the outside, it's currently 71.243.111.236, though we have a dynamic IP through our ISP, so that will change over time

---

### Post by dmizer on 2009-08-19
Your ISP may have port 80 blocked to prevent exactly this. There are ways to confirm this, but I don't recall immediately.

Edit:
It doesn't appear as though your router has an external IP address anywhere. Does your new ISPs modem also include routing ability? If so, you'll have to configure that router to forward port 80. You may also want to give it a unique subnet range so it doesn't conflict with your Linksys router.

---

### Post by Mesatchornug on 2009-08-19
> **dmizer said:**
> Your ISP may have port 80 blocked to prevent exactly this. There are ways to confirm this, but I don't recall immediately.

Except I can access the server. aarongrossman.com is live and visible right now.

My problem is that when I am on that machine it can't visit the internet. Every other machine on both subnets in the house can access the WWW, except this one.

---

### Post by dmizer on 2009-08-19
I see. The link to your site that you posted earlier has a ] at the end so it doesn't work. I assumed that was the problem. You're quite right, the page does indeed load once the correct URL is entered.

Check your server's IP address against all the other machines in your network. I suspect that you have two machines with the same IP address.

---

### Post by Mesatchornug on 2009-08-19
> **dmizer said:**
> I see. The link to your site that you posted earlier has a ] at the end so it doesn't work. I assumed that was the problem. You're quite right, the page does indeed load once the correct URL is entered.
hmmm. thank you, i'll see if I can go back and edit that now


> **dmizer said:**
> Check your server's IP address against all the other machines in your network. I suspect that you have two machines with the same IP address.

That seems rather unlikely, but I can check later. The primary router [a netgear unit IIRC] is set up with DHCP with an open range up to *.50. and the linksys "bridge" has DHCP from *.141+, meanwhile the server requests *.140 specifically.

the only things that were changed during the move are as follows:
*physical location
*ISP
*primary router

I copied all of the port forwarding settings from my old primary router to the new one, but it's certainly possible that I made a small configuration error there, so I'll be sure to check its settings when I arrive home this evening

---

