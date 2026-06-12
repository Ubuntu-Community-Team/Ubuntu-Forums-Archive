---
title: "strange wired ethernet behaviour, no connection"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by skew on 2010-05-18
I have a strange wired home network problem on a simple one cable
ethernet. 



The NIC cards and network use to work until lately. The computers NIC's 
are connected directly together with a twisted ethernet cable. I know the cable is functionally 
okay and the NIC cards show up correctly in ifconfig. Like I said this all worked once.



I set up interfaces as follows: 



Computer one (lucid)



auto lo

iface lo inet loopback



auto eth0 

iface eth0 inet static

address 192.168.1.3

netmask 255.255.255.0 



Computer two (karmic) primarily running mythtv



auto lo

iface lo inet loopback



auto eth0

iface eth0 inet static

address 192.168.1.4

netmask 255.255.255.0 



I've tried both interfaces with "gateway 192.168.1.1" and without it



If I ping computer two (192.168.1.4) from computer one (192.168.1.3) I get a result back 
which is not coming from the second computer but the first. If I detach the cable I can't 
ping that distant system at all. 



Broadband is not at issue in the mix as I don't have broadband available here. Here being just 20 minutes from the capital of Canada. Which IMHO is an embarrassment. For this country to leave so many of it citizens so cut off from high-speed Internet is ridiculous! (okay nuf said, I'll get off my soapbox now)
 

I have a WRT54G which is loaded with DD-WRT. I can connect to it with wires from both machines easily.


computer one <----> WRT54G OK     

computer two <----> WRT54G OK

Computer one <-----> computer two fails  



I also tried replacing static in the interfaces with dhcp it also fails. listing this when I /etc/init.d/networking restart



Internet Systems Consortium DHCP Client V3.1.3

Copyright 2004-2009 Internet Systems Consortium.

All rights reserved.

For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)



Listening on LPF/eth0/00:e0:b8:b8:cd:7e

Sending on   LPF/eth0/00:e0:b8:b8:cd:7e

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6

No DHCPOFFERS received.

No working leases in persistent database - sleeping.



ifconfig with dhcp in interfaces:



eth0      Link encap:Ethernet  HWaddr 00:e0:b8:b8:cd:7e  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:16 



eth1      Link encap:Ethernet  HWaddr 00:14:a5:ca:7c:15  

          inet6 addr: fe80::214:a5ff:feca:7c15/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:17 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1641 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1641 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:1007313 (1.0 MB)  TX bytes:1007313 (1.0 MB)



When I set the interfaces on computer one back to the static address above and
 attempt a connection to the second computer (192.168.1.4) with wicd it tells me I'm 
connected, see ifconfig below



eth0      Link encap:Ethernet  HWaddr 00:e0:b8:b8:cd:7e  

          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::2e0:b8ff:feb8:cd7e/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:16 



eth1      Link encap:Ethernet  HWaddr 00:14:a5:ca:7c:15  

          inet6 addr: fe80::214:a5ff:feca:7c15/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:17 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1673 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1673 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:1009633 (1.0 MB)  TX bytes:1009633 (1.0 MB)



As I said before when I ping it it returns a result, but the results are not coming from 
the computer I'm pinging but rather from the computer I'm pinging from. It seems to be some sort of loopback. I ran nmap which shows ports 
and services open on that distant computer which are not open or even installed on that computer.  I figure proves the ping results are false. 
Also the firewall has been turned off during all these attempts.


FWIW: I have tried every config permutation I can think of, as well the implementation of every 
diagnostic tool I know of (granted, not many of which I know how to use very well) plus all the hardware 
possibilities available to me from straight Ethernet cables, hubs, and switches boxes in every 
possible combination (countless times over) ;( .   And Yes, I do know that Google is my friend, sorta... 
and I've used it, BUT there is a thing called information overload and dealing with he said "try this" 

but she said "try the opposite" has muddied the waters for me enough at this point. 
So i though I would ask on this forum directly instead.
 

Does anyone have any help or suggestions? This has been driving me batty for a week now and I'm lost. I realize I'm a noob at networking but I don't recall having problems like this on any of my 
previous Ubuntu versions. Static had always worked in the past.  



Thanks all!

---

### Post by skew on 2010-05-20
*bump*

Anyone?!

---

