---
title: "how to set dynamic ip as gateway"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by kornphlake on 2009-11-18
I'm working on setting up a content filter using dansguardian.  I've got everything set up and running but right now I have my WAN interface (eth2) plugged into a router with a static ip assigned.  I'd like to plug directly into the modem so the network isn't double NAT'ed.  When I try doing this computers connected to the LAN interface (eth3) through a switch can't reach the internet because there isn't a default gateway.  With a static ip assigned to eth2 I'm able to use the ip for the "options routers xxx.xxx.xxx.xxx" dhcp3.conf file, with a dynamic ip the address is changing so what might work now will fail in an hour or two when the ip changes.

How do I set the "options routers" line in the dhcp3.conf file to use eth2 regardless of the ip assigned, rather than a specific ip?

I've searched but I must be searching the wrong terms because I can't find anything.

---

### Post by puppywhacker on 2009-11-18
you can use the static address for the server as "options router" the idea with ip-routing is hop-by-hop. So that you only have to route to the first node that knows "the way out" so if you set the modem to bridged mode, the server is a nat serving for the rest has on eth2 a real ip-address and on eth3 an internal address like 10.0.0.1 you can just let all the computers in your network use 10.0.0.1 as default gateway. You can not use an interface as ip-gateway.

---

### Post by kornphlake on 2009-11-18
Thanks, I was thinking of eth2 as a server rather than eth3, changed the router to the static ip for eth3 and everything is singing along perfectly.  Thanks.

---

