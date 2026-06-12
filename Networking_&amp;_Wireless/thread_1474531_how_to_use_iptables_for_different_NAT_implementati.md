---
title: "how to use iptables for different NAT implementation"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by RaMs39 on 2010-05-06
Hi 
If anybody worked on Iptables,please help me in implementing each type of NAT 
-Full Cone NAT 
-Restricted Cone NAT 
-Port Restricted Cone NAT 
-Symmetric NAT 
using IPTables. 
 
_Expalnation:_
 
•** Full Cone**: A full cone NAT is one where all requests from the same internal IP address and port are mapped to the same external IP address and port. Furthermore, any external host can send a packet to the internal host, by sending a packet to the mapped external address. 
 
• **Restricted Cone**: A restricted cone NAT is one where all requests from the same internal IP address and port are mapped to the same external IP address and port. Unlike a full cone NAT, an external host (with IP address X) can send a packet to the internal host only if the internal host had previously sent a packet to IP address X. 
 
• **Port Restricted** Cone: A port restricted cone NAT is like a restricted cone NAT, but the restriction includes port numbers. Specifically, an external host can send a packet, with source IP address X and source port P, to the internal host only if the internal host had previously sent a packet to IP address X and port P. 
 
• **Symmetri**c: A symmetric NAT is one where all requests from the same internal IP address and port, to a specific destination IP address and port, are mapped to the same external IP address and port. If the same host sends a packet with the same source address and port, but to a different destination, a different mapping is used. Furthermore, only the external host that receives a packet can send a UDP packet back to the internal host. 
 
On the netfilter mailinglist, Pedro Gonçalves suggested the following: 
192.168.2.170 is "public" address and 10.0.0.1 is "private" address
 
/-"Full Cone NAT", with the following rules:/
 
[HTML] 
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.2.170
iptables -t nat -A PREROUTING -i eth0 -j DNAT --to-destination 10.0.0.1
 
[/HTML]
/-"Port Restricted Cone NAT", with just a single rule:/
 
[HTML] 
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.2.170
[/HTML]
Please help me in implementing other NAT types.
 
Thanks in advance, 
RaMs

---

### Post by greybeard95a on 2010-12-25
So I have tried this for a full-cone NAT to my [diaspora pod]("http://graton.parts-unknown.org:3000") (which actually lives on my old laptop at 10.8.0.10 on an OpenVPN network)  And it still doesn't work.  What would prevent it?

I edited my existing firewall configuration to comment out my previous attempts and then proceeded as follows:

```
atlanta# iptables -F && iptables-restore < /etc/firewall.conf
atlanta# iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 74.207.227.150
atlanta# iptables -t nat -A PREROUTING -i eth0 -j DNAT --to-destination 10.8.0.10
```

I also tried flushing the configuration and running just the rules that should make the full-cone NAT work.  No joy.

---

