---
title: "Ubuntu 10.04 Servers lost internet connection with 2 active interfaces"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by preparationh67 on 2010-05-21
I have 3 Ubuntu 10.04 x86 servers. Each one has one connection that gets DHCP service from and server on a LAN network (eth0 on each machine), and one static connection that is tied to an external hostname (eth1) and goes out through a gateway to the internet. I had an issue a couple weeks ago that turned out to be the DCHP config file router request, which was messing up the servers and was fixed with a simple edit then everything was working great. However, Monday I could not ssh or ping any of the servers by their hostnames. When I got into the machines physically they could not ping either the local router or the external gateway and could not resolve any hostnames. I was eventually able to give them internet access through the local network by taking eth1 offline and undoing the previous change to the dhcp config file. One thing I did notice was the the resolve.conf file lists the names servers as the local loopback and 8.8.8.8 (google dns) and a search domain which is the domain of the local network. None of these servers are dns servers so could the resolve config file be whats messing up the networking? The 2 guys who also manage these servers who are well versed in linux networking aren't around right now so I'm pretty lost right now. Thanks in advance for any help you can provide.

---

### Post by Iowan on 2010-05-21
> **preparationh67 said:**
> ... they could not ping either the local router or the external gateway...By IP address or name (or neither)? Ordinarily, a machine receiving a DHCP address also receives DNS information from DHCP server. *Sometimes* the DHCP server maintains DNS information as well - if the machines provide their hostnames via */etc/dhcp3/dhclient.conf*.

---

