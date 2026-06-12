---
title: "IPsec-tools tunnel -- Access clients from gateway"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by Artemus on 2011-05-10
I have successfully established an ipsec tunnel between two LANS joined over the internet. The two LANS are 192.168.0.0/24 and 10.0.0.0/24. The gateways are 192.168.0.1(LAN)/xx.xx.xx.25(WAN), which connects to yy.yy.yy.11(WAN)/10.0.0.1(LAN) over the internet.  Hope that makes sense.

I can successfully ping between LAN clients. For example, 192.168.0.3 can ping 10.0.0.4. I can also ping from one LAN client to the other gateway on its (the gateways) LAN IP address. That is 192.168.0.3 can ping 10.0.0.1.

What I can't do is ping a client on the other LAN from a gateway. That is, 192.168.0.1/xx.xx.xx.25 cannot ping 10.0.0.4. I guess packets are getting routed to the WAN before IPsec sees them. Is there a way to get this to work? I think that an iptables rule will do it, but I don't know enough about iptables to write it.

Edit: I should add that I'm running ipsec-tools under Natty on the gateways.

---

### Post by Artemus on 2011-05-10
OK, I've made a bit of progress. I if I run

$ ping -I eth1 10.0.0.4 

on the 192.168.0.1/xx.xx.xx.25 gateway it makes it through the tunnel. So, it seems I need to route all packets intended for 10.0.0.0/24 through eth1 on that gateway. To do this, I tried


# ip route add 10.0.0.0/24 dev eth1

This didn't work, and in fact broke $ ping -I eth1 10.0.0.4 as well.

Anyone have any suggestions?

---

