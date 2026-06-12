---
title: "Ubuntu as a Router Problem"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by Craig1972 on 2011-01-12
Hi....

My ubuntu box is configured to use an IPsec tunnel for all traffic destined for the internet.  This tunnel is up and working fine and all my internet traffic is being routed through this tunnel.  

What I would like to do is have all my other LAN clients use this tunnel for their internet bound traffic.  How can I do this.  My other clients are currently connected to the internet via my linksys router/gateway...Here is What I have tried so far:

1)  enabled IP forwarding on my ubuntu box
2) altered my LAN clients gateway to use ubuntu box
3)  set masquerading ON the tunnel interface (ppp0)
4)  configured IP tables to allow forwarding from eth0 to ppp0 and ppp0 to eth0 
5) the ubuntu box has a route to the VPN server via my linksys router/gateway

This sort of worked, but I had had issues loading web pages etc....it just didn't work very well.  

What am I missing?

---

### Post by Craig1972 on 2011-01-12
Seems like this is related to MTU and ipsec fragmentation....setting the MTU on my windows client to 1352 seems to have resolved my issues.

---

