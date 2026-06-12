---
title: "no connection to part ofwired network"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by TwPlo on 2010-05-16
First of all: no problems under ubuntu 9.x.

Problem started with *fresh* install of Ubuntu 10.04 64 bit.

Internet access and e-mail are working. The router  (linksys 8 port V082) is responding and can access the router menu, all settings there are ok. 

But the problem is:

There are other network devices which are not accessible.
One of them is a telco Grandstream GXP2000 VoIP telephone.
The other problem device is a Brother HL-1670N printer.

If I log in onto the router, pinging the GXP2000 and the HL1670N works
If I ping from ubuntu out: 

> PING 192.168.1.* (192.168.1.*) 56(84) bytes of data.
From 192.168.1.% icmp_seq=1 Destination Host Unreachable
From 192.168.1.% icmp_seq=2 Destination Host Unreachable
From 192.168.1.% icmp_seq=3 Destination Host Unreachable
From 192.168.1.% icmp_seq=4 Destination Host Unreachable
From 192.168.1.% icmp_seq=5 Destination Host Unreachable
From 192.168.1.% icmp_seq=7 Destination Host Unreachable
From 192.168.1.% icmp_seq=8 Destination Host Unreachable
From 192.168.1.% icmp_seq=9 Destination Host Unreachable
From 192.168.1.128 i%_seq=10 Destination Host Unreachable
--- 192.168.1.* ping statistics ---
9 packets transmitted, 0 received, +11 errors, 100% packet loss, time 12025ms
, pipe 4

Ifconfig tells that eth0 is configured correctly.

> eth0      Link encap:Ethernet  HWaddr 00:**:d*:54:**:5* [COLOR=Blue] (mac address)  [/COLOR]
          inet addr:192.168.1.%  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe%::21f:d*:**:*54:295e/64 Scope:Link    [COLOR=Blue]just the IPV6 IP[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95623492 (95.6 MB)  TX bytes:18204870 (18.2 MB)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/% Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76858 (76.8 KB)  TX bytes:76858 (76.8 KB)

So the 192.168.1* is not responding.
The % is the IP number of the computer that runs ubuntu 10.04

I still have windows 7 64bit on another computer and windows7 has no problem.

The external router blocks nothing from lan to wan, also nothing within the lan or the windows machine should also have the same problem.


Test from the windows machine: the printserver of the HL1670N shows up.
The server from the GXP2000 shows up

It's just ubuntu 10.04 that has the problems.

I've rebooted the router  and the compouter   but problem stays. I will install ubuntu 10.04 also on the windows machine to check if it could be hardware related, Intel board versus amd board.


Meantime, any hints are welcome.

---

