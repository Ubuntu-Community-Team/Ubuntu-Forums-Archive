---
title: "DHCP troubles with ADSL modem"
date: 2005-01-19
forum: Networking &amp; Wireless
---

### Post by Rodelgrim on 2005-01-19
Hi, 
I'm experiencing very annoying troubles with my Dlink DSL-300T ADSL modem (PPPoA) and Ubuntu. The connection goes great for some time (maybe a long time), then the DHCP stops working. In fact for some reason at a certain point the modem does not respond to my DHCP requests, my eth0  loses its address and the modem begins flooding me with ARP requests (it cannot find me either, since at that point I do not have any IP address). Then, for some reson, after some time, the modem does respond to the n-th DHCP request and the connection goes again pretty well until the next DHCP timeout. Obviuosly I've discovered this by some sniffing with Ethereal.

I've already fixed the static DNS problem, commenting the row in dhclient-script in which resolv.conf is overwritten and blanking dhclient.conf. 

I've noticed one time that, having had no response from the modem's DHCP server, the pc  sent an ICMPv6 neighbour discovery (server solicitation) message (which the modem could not understand, I believe). So, I've tried to remove ipv6 module, uncommenting it in /etc/modutils/aliases and giving an update-modules (so /etc/modules.conf has ipv6 commented too). Unfortunately, after rebooting, that has not worked, and I still have the ipv6 module on.

I do not tried to install pump. 

I have firestarter installed, but I don't think it can do all this mess (no, it does not drop DHCP packets)

Thanks A LOT,

Rodelgrim

PS: the modem should be ok, since I've used it successfully for 9-10 hours last day with my iBook - OSX 10.3.3.

---

