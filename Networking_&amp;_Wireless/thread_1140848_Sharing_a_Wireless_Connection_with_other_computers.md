---
title: "Sharing a Wireless Connection with other computers"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by nvikram on 2009-04-28
Hi Guys,

I am currently using ubuntu 9.04 and I am trying to connect this computer to a router, so that other machines can connect wirelessly. When I used to run windows XP, I could just share the wireless connection and then use Ethernet to connect my computer to the router and it worked. IS there anyway to do this in ubuntu?

Thanks so much :)

---

### Post by f37u5g0d on 2009-04-28
Yeah you have to configure iptables.  Iptables is a irremovable part of the kernel that makes your machine a network server.  It is rather difficult to configure however :(.  You can get started by running man iptables and then googling for a good how to.  There are good ones out there.  Also you probably want to set up a dhcp server (not as hard) just find the appropriate package.  This will allow clients to connect to your network without selecting their own IP address (what everyone in the world is used to).  Any more questions?

---

