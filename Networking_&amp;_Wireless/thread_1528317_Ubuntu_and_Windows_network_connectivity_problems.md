---
title: "Ubuntu and Windows network connectivity problems"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by mnox on 2010-07-10
Hello. I'm trying to connect two PCs to the Internet (or at least to create a local network) using a crossover cable.

My main PC (the one that has two ethernet adapters and is connected to the Internet) runs Windows 7 and my secondary PC runs Ubuntu 10.04. I set their IP addresses and Subnet masks manually:

Windows PC:
IP: 192.168.0.1
Subnet Mask: 255.255.255.0

Ubuntu PC:
IP: 192.168.0.2
Subnet Mask: 255.255.255.0

Unfortunately, it doesn't work. Both systems send out packages but don't receive anything. 

How can I possibly fix this, so that I could use LAN and share the Internet connection between PCs? Does Windows need special  software to recognize Ubuntu (or the other way around)?

THANK YOU. Not sure what I did, but it works now.

---

### Post by Iowan on 2010-07-10
I haven't used Win7 yet, but I suspect (like it's predecessors) it has connection sharing. Check **ifconfig -a** to verify the Ubuntu machine actually has an IP address. You might also check results of **route -n** to see what address is used as the gateway.

---

