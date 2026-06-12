---
title: "Configure network with MaaS server and dnsmasq"
date: 2012-09-28
forum: Networking &amp; Wireless
---

### Post by Fajkowsky on 2012-09-28
I follow instalation from here wiki.ubuntu.com/ServerTeam/MAAS and 
I decide to do something like this:
[Attached file]
And on MaaS server i install dnsmasq and make it DHCP server. 

I leave this blank. And in etc/network/interface I have this:


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

And on nodes there is no connection outside local network. Like server is blocking traffic but it has internet connection.

---

