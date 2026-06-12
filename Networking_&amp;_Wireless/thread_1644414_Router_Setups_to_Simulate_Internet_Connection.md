---
title: "Router Setups to Simulate Internet Connection"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by salukibob on 2010-12-13
Hi There,

Apologies if this isn't really an Ubuntu question. I just think its likely someone here will know the answer...

Simply put, I want to simulate two home networks, connecting together over the internet. The simulation will ultimately include IPSec vpn, but for the moment, I just want to be able to ping from one local network to the other, over the 'internet'.

I have two netgear routers. One is setup for local addresses on the 192.168.0.0/24 network, with a single wan port set to 172.16.0.1/24. The other is setup for the 192.168.1.0/24 network with a single wan port set to 172.16.0.2/24. Any host connected to either of the networks configures via dhcp, so gets the router as its gateway.

Firstly, does it make sense to connect the two router wan ports together? Or do I really need a third router to simulate my ISP?

Secondly, how do I setup the routing so that a ping would work correctly,  i.e. from host 192.168.0.5
# ping 192.168.1.10


Thanks for any help with this,
Regards
Rob Smith

---

