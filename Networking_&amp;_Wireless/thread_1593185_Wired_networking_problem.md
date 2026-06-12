---
title: "Wired networking problem"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by Nottawa on 2010-10-11
I am unable to get my wired network connection to work.  My wireless works great.  My laptop sees the wired connection, but will not connect.  I am running 10.04 on a Lenovo T400 with 3 gb of ram.

Any suggestions will be appreciated.

---

### Post by Iowan on 2010-10-11
To what are you connecting? I presume **ifconfig -a** shows no IP address - if you are trying to get DHCP address, you might post results of **sudo dhclient eth0** (assuming that's the name of the wired interface).

---

### Post by Nottawa on 2010-10-13
Iowan:  Thanks for thinking about my problem.

When I enter the first request you posted, I get the following response:

peter@peter-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:7e:db:b5:9f  
          inet6 addr: fe80::224:7eff:fedb:b59f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3234 (3.2 KB)  TX bytes:3330 (3.3 KB)
          Memory:fc600000-fc620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66841 (66.8 KB)  TX bytes:66841 (66.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:76:28:4c  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe76:284c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48899010 (48.8 MB)  TX bytes:11135271 (11.1 MB)


In respose to the second query, I get this:

peter@peter-laptop:~$ sudo dhclient eth0
[sudo] password for peter: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:24:7e:db:b5:9f
Sending on   LPF/eth0/00:24:7e:db:b5:9f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.2.17 from 192.168.2.1
DHCPREQUEST of 192.168.2.17 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.17 from 192.168.2.1
bound to 192.168.2.17 -- renewal in 577541 seconds.
peter@peter-laptop:~$ ^C

I hope you have some insights for me.  I probably should have posted this in the Newbie section but went here first.
Thanks

---

### Post by Iowan on 2010-10-13
> **Nottawa said:**
> I hope you have some insights for me.  I probably should have posted this in the Newbie section but went here first.
ThanksEither place will work...
After you ran **dhclient**, did you have any luck? It looks like eth0 got an IP address... but it's in the same subnet as wlan0 (which will likely cause routing problems.)

---

### Post by Nottawa on 2010-10-13
Unfortunately, no joy yet.  If I am having an ip address conflict, how do I change one of them?  Even if I turn off the wireless, I still don't connect via the wired network.

Peter

---

### Post by Iowan on 2010-10-13
If you turn off wireless and restart/reboot. Does eth0 get an address? If you run **dhclient** and eth0 gets an address, what is result of **route -n**? Also, can you ping router (via eth0?)

---

### Post by Nottawa on 2010-10-13
I don't think anything changed.  Here are the results:

peter@peter-laptop:~$ sudo dhclient eth0
[sudo] password for peter: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:24:7e:db:b5:9f
Sending on   LPF/eth0/00:24:7e:db:b5:9f
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.17 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.17 from 192.168.2.1
bound to 192.168.2.17 -- renewal in 467785 seconds.

and:

peter@peter-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0

and:

peter@peter-laptop:~$ ping
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination


Thanks for your help.  I'll check back for your answer tomorrow.

Peter

---

### Post by Iowan on 2010-10-13
Well... the wireless still activated, got an address, AND a gateway. The ping command would have (probably) been:```
ping 192.168.2.1
```Having two gateways usually causes problems with routing. You might be able to disable wireless by right-clicking on Network Manager applet.

---

