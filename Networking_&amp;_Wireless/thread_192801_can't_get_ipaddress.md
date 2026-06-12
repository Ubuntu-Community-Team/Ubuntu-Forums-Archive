---
title: "can't get ipaddress"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by stu2004 on 2006-06-09
hi,

I have installed 606. In the networking settings i have an active ethernet card, dns servers are set and i can see the network.

I can't seem to get a dhcp ipaddress. I assume my lack of knowledge here is the problem, what have i failed to do?

---

### Post by abovett on 2006-06-09
Hi

I'm a bit confused by your question. What do you mean by "I can see the network"? If you haven't got an IP address you won't be able "see" anything else on the network.

As for DNS servers - setting them won't help you get an address from a DGCP server. In fact, in most cases the DHCP server will provide both,IP address, the DNS servers, and the gateway address.

What are you using as a DHCP server by the way? Is it a router/broadband mode or what? Do you know it's functioning as a DHCP server? Have you tried using a static IP address and does it work when you do?

If you need more help with this. perhaps a good start is to open a terminal (Applications -> Accessories -> Terminal), type "ifconfig" (no quotes) and post the results.

Cheers

Andy B

---

