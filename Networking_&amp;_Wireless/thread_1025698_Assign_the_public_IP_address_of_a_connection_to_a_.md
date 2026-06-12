---
title: "Assign the public IP address of a connection to a LAN device"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by borobudur on 2008-12-30
Hi, I'm installing my server machine to a new internet connection. 

I have the problem that I can't chose the machine in the routers list of devices (configuration menu) to assign the external IP to the server. 

I gave the server static addresses in */etc/network/interfaces*. I was thinking perhaps I need to allow hosts too, so I set in* /etc/hosts.allow* ALL: LOCAL, but still I can't. 

Any idea?

---

### Post by borobudur on 2009-01-03
Okay, I found out what's the problem. I had to create a new interface with the following command:
```
pppoeconf
```So I have a interface eth0 with the static set local IP (192.168.1.xx) and a interface ppp0 with the public external IP. 
Almost everything works fine just a odd thing is still there. I can receive some sites like:
[en.wikipedia.org]("http://ubuntuforums.org/en.wikipedia.org")
[www.gmx.ch]("http://www.gmx.ch")
but I don't receive anything from site like:
[www.ubuntuforums.org]("http://www.ubuntuforums.org")
[www.nzz.ch]("http://www.nzz.ch")

I didn't had this before my server did work yet.
What could that be?

---

### Post by borobudur on 2009-01-08
I was playing around with the MTU value and set it allover to 1492 but no success:
```
sudu ifconfig eth0 mtu 1492
```
Any other idea?

---

### Post by borobudur on 2009-01-08
Here my interfaces:
```
eth0      Link encap:Ethernet  HWaddr 00:e0:18:a4:31:e3  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fea4:31e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:76648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5756284 (5.4 MB)  TX bytes:733012 (715.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:151794 (148.2 KB)  TX bytes:151794 (148.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:212.147.x.x  P-t-P:212.147.x.x  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2771 (2.7 KB)  TX bytes:2363 (2.3 KB)
```I see that error when I restart the network:
```
dsl-client: error while getting interface flags: no such device
```

---

### Post by kestrel1 on 2009-01-08
> **borobudur said:**
> 
Almost everything works fine just a odd thing is still there. I can receive some sites like:
[en.wikipedia.org]("http://ubuntuforums.org/en.wikipedia.org")
[www.gmx.ch]("http://www.gmx.ch")
but I don't receive anything from site like:
[www.ubuntuforums.org]("http://www.ubuntuforums.org")
[www.nzz.ch]("http://www.nzz.ch")

I have the occasional problem with the Ubuntu forum. In fact only tonight I was unable to get on to the site for a good ten minutes. I was just getting an error that my request couldn't be forwarded at this time, but all other sites worked OK.
What's the output from:
```
dhclient
```

---

### Post by borobudur on 2009-01-09
It's 50% of all sites which I can't receive in my LAN.

How can I get the output from my server? Over ssh I loss the connection after calling dhclient, so I don't see the whole output. Then I thought I write the output into a file:
```
sudo dhclient > output.txt
```But the file stays empty. Do you have an other way?

Well, here is what I get over ssh:

```
user@machine:~$ sudo dhclient > dhclient-output.txt 
[sudo] password for user: 
There is already a pid file /var/run/dhclient.pid with pid 29988
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
```

---

### Post by aeronotix on 2009-01-09
Have you tried disabling IPv6?

---

### Post by borobudur on 2009-01-09
How do I do that? 

But if that would be the problem, anything would work, right?

---

### Post by borobudur on 2009-01-10
Turned off the ipv6 but still the same :-(

I reconfigured the interface with *pppoeconf* again and I realized that this screen describes exactly my problem, but I haven't found the solution yet.

[IMG]http://users.telenet.be/Asterisk-PBX/Images/InstallPPPoE10.jpg[/IMG]

Added the MTU and MRU 1412 to dsl-provider but no success.

I installed the pppoe connection on my laptop and there I have exactly the same problem, so it shouldn't be a messed up system.

---

### Post by borobudur on 2009-01-15
Here the output in debug mode when I start the interface
```
user@machine:~$ sudo pon dsl-provider 
Plugin rp-pppoe.so loaded.
PADS: Service-Name: ''
PPP session is 4
using channel 18
Using interface ppp0
Connect: ppp0 <--> eth0
sent [LCP ConfReq id=0x1 <mru 1412> <magic 0xb3d0600d>]
rcvd [LCP ConfAck id=0x1 <mru 1412> <magic 0xb3d0600d>]
rcvd [LCP ConfReq id=0x2 <mru 1492> <auth pap> <magic 0x1103199e>]
sent [LCP ConfAck id=0x2 <mru 1492> <auth pap> <magic 0x1103199e>]
sent [LCP EchoReq id=0x0 magic=0xb3d0600d]
sent [PAP AuthReq id=0x1 user="me" password=<hidden>]
rcvd [LCP EchoRep id=0x0 magic=0x1103199e]
rcvd [LCP ConfReq id=0x1 <auth pap> <magic 0x4666a2d5>]
sent [LCP ConfReq id=0x2 <mru 1412> <magic 0xdff6afb1>]
sent [LCP ConfAck id=0x1 <auth pap> <magic 0x4666a2d5>]
rcvd [LCP ConfAck id=0x2 <mru 1412> <magic 0xdff6afb1>]
sent [LCP EchoReq id=0x0 magic=0xdff6afb1]
sent [PAP AuthReq id=0x2 user="me" password=<hidden>]
rcvd [PAP AuthAck id=0x2 ""]
PAP authentication succeeded
peer from calling number 00:18:F6:72:41:1B authorized
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr 212.254.x.x>]
sent [IPCP ConfAck id=0x1 <addr 212.254.x.x>]
rcvd [IPCP ConfNak id=0x1 <addr 212.147.y.y>]
sent [IPCP ConfReq id=0x2 <addr 212.147.y.y>]
rcvd [IPCP ConfAck id=0x2 <addr 212.147.y.y>]
not replacing existing default route via 192.168.1.254
Cannot determine ethernet address for proxy ARP
local  IP address 212.147.y.y
remote IP address 212.254.x.x
```

---

### Post by borobudur on 2009-01-16
Well, I can't find the solution with ppp but I found the problem with the ip-forwarding (NAT): I gave the server an static ip which the router didn't like, it was in the range of the dhcp-server of the router.

---

### Post by borobudur on 2009-01-21
Can't fix the ppp problem but I made it with NAT. There the problem was that I gave a static ip to the server which was in the range of the dhcp-server of the router.

---

