---
title: "PPTPD VPN and Linux firewall problems"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by digitalsushiuk on 2011-01-17
Hi guys hope you can help me with this problem that has been annoying me all week. I am fairly new to linux but have managed to get most things setup aside from this

Here is the setup, Ubuntu Server 10.04.1 Working as internet router/firewall/filter.

System has 3 nics, eth0 (external ip), eth1 & eth2 (internal networks) masquerading to eth0 with ipv4 routing enabled.

I set up PPTPD server to service VPN incoming on eth0, opened port 1723 and the GRE protocol on the INPUT filters of linux iptables firewall. This allowed vpn connections to be made fine (well sometimes it can take 2 attempts but i can live with that). However no traffic can flow through the vpn, i.e. I cannot connect to internal servers at all.

I have discovered it seems to be the firewall that stops this, if I set the default action for forward packets to accept, it works fine. set the default action to drop and although the VPN connection is made it doesn't work. The ppp interface is made (usually ppp0) and can be pinged by the internal network.

Can anyone point me in the right direction as to what rule i need to add to forward packet filter to allow traffic from the vpn interface to the internal network as i would rather not leave the default forward rule as accept.

Cheers in advance, if you need any more info then please ask.

---

