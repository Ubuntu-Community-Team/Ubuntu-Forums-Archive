---
title: "Connected but can't surf"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by Bazmataz on 2009-12-27
Hi I have just installed Ubuntu 9.10 fot the first time but am having problems surfing the net. It connects to the ethernet modem modem and I can load 1 or 2 pages then it stops loading. The connection works fine when I boot into Vista.

I am using an ASUS P5S-MX SE with a SIS968 gigabit ethernet and the driver in ubuntu shows up as SIS 190. (In windows it uses an SIS 191 driver but I think they use the same driver 190/191).

I have an IP and when I ping ubuntu.com from the the tool I get 100% succes.

I ran ifconfig and got 

eth0      
Link encap:Ethernet  
HWaddr 00:1d:60:66:fb:f1  
          
inet addr:119.94.252.78  
Bcast:119.94.255.255  
Mask:255.255.240.0
          
inet6 addr: fe80::21d:60ff:fe66:fbf1/64 Scope:Link
          
UP BROADCAST RUNNING MULTICAST  
MTU:1500  Metric:1
          
RX packets:49 errors:2 dropped:0 overruns:0 frame:2
          
TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:12989 (12.9 KB)  TX bytes:5937 (5.9 KB)
          
Interrupt:19 Base address:0xdead

All settings are default, DHCP is automatic.
This is the first time I have used linux so compiling stuff is beyond me.
any help is appreciated. Thanks in advance.

---

### Post by Iowan on 2009-12-27
A couple more things to check: **route -n** should show your default gateway on teh last line, and */etc/resolv.conf* should contain the address of your nameserver (maybe more than one).

This has no bearing on the problem, but I always find it somewhat interesting to see the  base address of a non-working interface as: > **Bazmataz said:**
> 
Interrupt:19 Base address:[COLOR="Red"]0xdead[/COLOR]


---

