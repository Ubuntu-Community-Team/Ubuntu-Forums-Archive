---
title: "New network setup help"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by saint luke on 2009-12-29
Hi all,

I need some help setting up a network im trying to reconfigure. Its currently 3 XP, 1 W7, 1 OSX 10.6, & 1 OSX 10.4 running off a wireless router. Im chaning it to run through a linux server for a few reasons, but are having troubles getting the connection to share over the network.

The server is running 9.1 desktop with 2 ethernet cards, and since i have 3 of them lying around, i was going to use 1 wired modem/router (netgear DG834) as the modem, and the wireless modem/router (DG834PN) as the router. This is one area im not entirely sure about...

For the "modem" i have disabled NAT, and left DHCP enabled (i would have thought disable this but i couldnt access the internet even when directly connected to it). For the "router" i have disabled both. One problem i have found is that they both want to use 192.168.0.1 as the default IP address. If i change one or both, they both wont work together which i cant work out why. Left untouched, im unsure what the 2nd ip address changes to, but they work.

I have the modem set as eth0 and the router as eth1. The guide i used to setup ubuntu was here (ive not used any linux before) - [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) . I followed that word for word, with the only changes ive made were to the ip addresses of eth0 (192.168.0.10) and eth1 (192.168.0.11). The other change were to the DNS server, which i set what it was previously as 61.9.211.33 & 61.9.188.33. - This im also thinking might not be right, so some some help here would be great

Setup like this, they both appear to be working fine, internet works on the server, and network is up and able to be connected to.

From there i went to the W7 computer, found the wireless network, connected fine. Setup tcp/ip to be

IP - 192.168.0.20
SUBNET - 255.255.255.0
GATEWAY - 192.168.0.11 (tried .10 just in case i got that part wrong)
DNS - 61.9.211.33 & 61.9.188.33

Thats where im stuck, the w7 computer connects to the network fine, the server can access the internet fine, but it isnt getting shared across the network for whatever reason i cant determine. Any help would be appreciated!

Cheers

---

### Post by Iowan on 2009-12-29
Having both interfaces in the same subnet is probably confusing the server. Somehow, one of the modem/router's needs to use a different subnet.

---

### Post by saint luke on 2009-12-30
i changed the one im using as a router to 255.255.0.0 to no avail

I can connect to the 'router' with my w7 computer, where i changed the ip address to 192.168.1.0. Went back to the server but it couldnt connect.

Im sorta heading to the point where i buy an actual router rather than disabling the modem function of one of the modem routers, as it appears its causing conflicts...

---

