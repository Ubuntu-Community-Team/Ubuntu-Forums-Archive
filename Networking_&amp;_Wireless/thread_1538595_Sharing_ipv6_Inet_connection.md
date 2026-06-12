---
title: "Sharing ipv6 Inet connection"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by just_another_user on 2010-07-25
Hi,

I'm using Internet connection through local network, receiving white (global) IP, route, DNS with local DHCP server.  

Lately I noticed that my Ubuntu gets ipv6 autoconfiguration from ISP router, receiving global ipv6 address and automatically adding ipv6 route. I can access Internet resources using ipv6 connection: 
I can ping inet resources using my ipv6 global address and access, for example, ipv6.google.com or [http://wattcher.015.info/ipv6.html](http://wattcher.015.info/ipv6.html).

Question is:
How can I share ipv6 connection to my home network? 
Using ipv4 it's easy, I just can use NAT for this. But if I understand correctly, in ipv6 there isn't such thing as NAT, because there is no limit in ip addresses. 

Thanks

---

### Post by sanderj on 2010-07-26
What are the first 8 bytes of the IPv6 address [http://wattcher.015.info/ipv6.html]("http://wattcher.015.info/ipv6.html") is reporting?

If it's 2001:0: (or 2001:0000:), it's miredo/terdo, which is hard if not impossible to share with other computers on your LAN.

---

### Post by wiz561 on 2011-02-04
I'm in a similar situation and mine isn't 2001:0000, it's 2001:400:.

How does one go about forwarding this onto your internal LAN?  I've setup radvd to share the address, and I can ping ipv6 addresses on the gateway host, but can't ping anything from my local lan.

I was told that my ISP has to assign another /64 block to the other VLAN's (even if it's 192.168 private ip space).



Thanks!

---

