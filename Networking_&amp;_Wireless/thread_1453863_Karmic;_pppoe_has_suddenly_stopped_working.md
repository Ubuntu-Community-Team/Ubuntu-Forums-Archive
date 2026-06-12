---
title: "Karmic; pppoe has suddenly stopped working"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by kita on 2010-04-13
I have a DSL connection and since Ubuntu 9.10 my connection require pppoeconf setup. This worked reasonable fine for a while.

This morning, on restart, my Internet stopped working. I cannot ping any sites.

"plog" returns:

Connect ppp0 <--> eth0
PAP authentication success
Peer from calling number [###] authorised
cannot determine ethernet address for proxy ARP
local IP [###]
remote IP [###]
primary DNS [###]
secondary DNS [###]

which is exactly what I used to get when my internet used to work. (I'll fix the proxy ARP thing another time right now all I want is the net back)

I recently botched a postfix setup. That might have messed up something but i'm not sure. I've checked hosts, hosts.conf, resolv.conf, my dsl-provider file in /etc/peers/ppp. Nothing is making sense to me anymore and I dont know whats wrong! This is kindof urgent as I need to be able to do my project today -- Please Help?

---

