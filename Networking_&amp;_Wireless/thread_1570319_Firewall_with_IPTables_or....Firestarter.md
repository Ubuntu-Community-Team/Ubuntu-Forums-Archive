---
title: "Firewall with IPTables or....Firestarter?"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by AgentViper on 2010-09-08
I am setting up an Ubuntu box to be my firewall for my home network.  I am having some issues to start.  A friend who is a network engineer told me that I need to turn on IP forwarding (I added a NIC to the box...total of 2 now).  So my question is...I plug the cable model CAT5 to one NIC, and then have the other NIC go to my router?  Or should that go to a switch and then to a router?

Also what is the best firewall to use....IPTables or Firestarter?  I have never used IPTables before.  


-Viper

---

### Post by BkkBonanza on 2010-09-08
Either way will work but you will have to configure to suit which way you choose.

Why have the router and firewall separate? If you're going to dedicate a machine to firewall why not have it do the routing too? 

The difference in config between firewall and firewall+router is negligible.

Anyway, typically in a dedicated application like this you would use iptables alone. iptables is just a utility for modifying the kernel routing tables (netfilter).

Firestarter, UFW etc. are all simplified user overlays to iptables. If you want to really understand how the router/firewall function work then you need to figure out iptables (which isn't hard, it's just there is a lot of very poor tutorials around on it and they don't explain anything except do this, do that). These simplified user interfaces are typically more oriented to desktops than routers, so you may will end up doing low level stuff anyway. It's better to understand it than copy/paste other peoples mistakes.

So you have,

1. WAN -> Firewall -> Router -> Switch -> all your toys
(Firewall passes everything to router IP for routing. Router does DHCP/DNS)

2. WAN -> Firewall+Router -> Switch -> all your toys
(Firewall does the routing itself, and has a DHCP srv / DNS fwd)

3. WAN -> Firewall -> Switch -> Router -> other toys too.
(Really same as 1 except traffic doubles on LAN)

---

### Post by AgentViper on 2010-09-11
Thanks.  So I am doing Modem > Ubuntu firewall box > Router

I enabled IP Forwarding and it's not working.  I did this:

/etc/sysctl.conf:
net.ipv4.ip_forward = 1

I connected the modem to one NIC and then my router to the other.  I don't see to be getting any IP for either NIC.
Before I did this setup I edited my network interface record and set DHCP for both NICs.  Do I need to remove this?

Viper

---

### Post by BkkBonanza on 2010-09-11
You can only set DHCP if there is a DHCP server running on each side. If no DHCP servers then you would need to configure manual IPs. Typically on the modem side your ISP would have DHCP and so shoulod assign an address. Also, typically a router would only offer DHCP on the LAN side. So the modem<->router link would require static IPs for both ends.

---

### Post by lisati on 2010-09-11
Firestarter isn't a firewall, it's a front end for ipTables. A lot of people recommend UFW instead of Firestarter these days.

---

