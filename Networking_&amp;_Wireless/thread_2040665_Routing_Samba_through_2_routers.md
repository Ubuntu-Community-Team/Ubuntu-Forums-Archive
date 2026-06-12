---
title: "Routing Samba through 2 routers"
date: 2012-08-11
forum: Networking &amp; Wireless
---

### Post by Valuk on 2012-08-11
I'm currently living in a house with 2 separate internet connections, each with their own routers.  My desktop is running Kubuntu 12.04, and I am trying to allow all users access to Samba.  I have connected an ethernet cable between the two routers, but I can't figure out how to set them up so systems on one router can access my system on the other router.  Also, don't want internet access shared between networks.

Anyone know how to make this possible?

Router my desktop is connected to:  Netgear WNDR4500
Other Router:  Netgear WPN824N

---

### Post by SeijiSensei on 2012-08-11
Assuming the two networks have non-overlapping private network addresses, e.g, 192.168.1.0/24 and 192.168.2.0/24, then you'll need to add a static route to each router that points to the other router as the gateway to its network.  You'll need to add a rule to each router that accepts traffic from each network as well.  You might also have to futz with the routers to insure that none of this local traffic is masqueraded with "network address translation," or "NAT."

If you only want to enable Samba, then you can block the limited network from access to anything other than ports 137-139 and 445.  All these ports should be open to TCP connections.  I'd throw in UDP access to 137-138 as well, since some versions of the Microsoft protocols use those for browsing I believe.

---

### Post by Valuk on 2012-08-11
I can't figure out how to set this up correctly.  I'm trying to get the two networks bridged, so devices can communicate between them (i.e. gaming, file sharing, etc.) without sharing the internet access.  I really don't know that much about networking, just a bit, so I might need things explained/dummed down.

---

### Post by Valuk on 2012-08-11
I have run out of time, and as such, will look to other solutions.  I thank the one reply, it is unfortunate I was unable to solve this issue with the help given.

---

### Post by bakegoodz on 2012-08-12
The way I would do it is put another network card in the file server. So 1 interface on each network. If the networks have different network ranges you will not need to configure the routers, other wise you will need to configure one. (example 192.168.0.x and 192.168.1.x) You want to setup one interface manually so it will not to have a gateway and DNS. The interface with gateway and DNS will give the samba server Internet access.

---

