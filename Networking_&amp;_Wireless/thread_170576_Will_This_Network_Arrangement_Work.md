---
title: "Will This Network Arrangement Work?"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by crumja on 2006-05-04
Hi,

I've scoured the web for info about this setup, but it seems that hardly anyone wants to implement it.

Basically, I have a server that I'd like to act as a firewall and squid server for my home network of 4 pcs. I have a wireless router, a netgear mr814 that I think I'll be using as the "hub/switch." I want the internet to go through my firewall (with 2 ethernet cards) and have the firewall connect to the router, which would then route the connection to my pcs. The router should also be able to handle wireless accesses.

My questions come down to whether a router can be used in this manner - as a dumb switch and whether I can access my firewall from inside the network. I've had problems before trying to connect to something just one level above my gateway. What specific config do I have to do?

Thanks

---

### Post by neouser99 on 2006-05-04
heres what i am doing and would highly recommend

i have 5 comps, 2 of them wireless, and one server. my server has 2 nics in it, similar to yours, one to the net (cable modem) and the other to a 16port switch. hanging off the switch are the 3 connected pcs and the wireless access point. with it in access point mode it will just bridge the connections. on the server i am running shorewall (extremely IMHO easy to configure for nating and everything), dhcp, bind, etc. a squid would be easy to plug into this setup. i also have numerous other things, apache, mysql, ssh (duh), rsync, etc. all of this works awesome, no problems what so ever.

so i guess, yea, it works, if you need any more help let me know

-neo

---

### Post by crumja on 2006-05-05
Interesting arrangement. I can see how that would work. What I'm wondering now is whether a router would function as a switch, e.g. dumbed down.

---

### Post by neouser99 on 2006-05-05
yes, it should. if you turn off dhcp on most consumer routers (linksys, dlink, etc) they will disable the wan port and the 4-5 lan ports will act as a switch. just make sure nothing goes to the WAN interface.

-neo

---

### Post by mips on 2006-05-05
[QUOTE=crumja]Interesting arrangement. I can see how that would work. What I'm wondering now is whether a router would function as a switch, e.g. dumbed down.[/QUOTE]


Should be ok if you put it into "bridged mode", and turn off all the dhcp/dns/nat stuff.

---

