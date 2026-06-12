---
title: "PPTP VPN Routes"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by kylebk on 2009-12-13
Hello, I am trying to connect to the ipredator VPN service with ubuntu 8.04 desktop. I am attempting to create the connection manually (with the help of webmin for autoconnect), and so far I am able to get it to connect, but I am not sure what rules to use to route data through the VPN (I would like to route all data through it).

Dec 13 13:01:56 serv1 pppd[13830]: Using interface ppp0
Dec 13 13:01:56 serv1 pppd[13830]: Connect: ppp0 <--> /dev/pts/2
Dec 13 13:01:58 serv1 pppd[13830]: CHAP authentication succeeded
Dec 13 13:01:59 serv1 pppd[13830]: MPPE 128-bit stateless compression enabled
Dec 13 13:01:59 serv1 pppd[13830]: local  IP address 93.182.150.60
Dec 13 13:01:59 serv1 pppd[13830]: remote IP address 93.182.150.2

It seems to be connecting correctly, and the interface ppp0 appears in my ifconfig.

When I first connect, a rule is added to my routing table that seems to cause a packet looping issue: [http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lots_of_data](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lots_of_data)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
93.182.150.2    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


If I remove that route, the connection seems fine and stays up.

I would like to know what routes I should use to route all network data through the vpn connection. Thanks

---

