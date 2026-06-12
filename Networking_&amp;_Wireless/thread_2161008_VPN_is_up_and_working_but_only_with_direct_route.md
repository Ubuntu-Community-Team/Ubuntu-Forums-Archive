---
title: "VPN is up and working but only with direct route"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by sebrock on 2013-07-09
So I have a VPN (L2TP/IPsec) up and running. The interface (ppp0) is assigned an IP and I can see keep-alive messages being sent and answered. However it only works if I make a direct route to a specific address with the ppp0 interface as a gateway. If I try to ping an arbitrary IP though the interface no answers are received. What I would like to do is to have the transmissionbt-daemon bind to the ppp0 interface and use my normal eth0 interface for anything else (webserver etc.)

The default route is as of now going to eth0. I am sitting behind a router with NAT. I'm not sure on how to proceed to debug this. I don't even know where messages are being stuck although I guess it's on the way back. Any tips on how to proceed are greatly appreciated.

route -n:

[PHP]128.XXX.105.X   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0[/PHP]

---

### Post by sebrock on 2013-07-19
So I followed this and it all worked out fine:

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/]("http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/")

---

