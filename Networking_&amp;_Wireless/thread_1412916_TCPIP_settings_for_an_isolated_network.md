---
title: "TCP/IP settings for an isolated network?"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by alunde on 2010-02-21
I'm trying to help someone at a small non-profit set up an isolated network for a classroom, not connected to the Internet.  Most of the computers are old second-hand systems, made usable by running Linux, the one new computer can dual boot Ubuntu and Windows.

I think the most light-weight approach would be to use one of the network numbers reserved for private use, assign static IP addresses, and host names in a hosts file, rather than relying on DHCP or DNS, because this wouldn't rely on any servers.

But, even so, I expect to have to configure _something_ for the IPs of a gateway and DNS servers when we set up the static IP settings.

My question is what would work best for these settings? 

The best guess I can make would be to list a real system with a tcp/ip stack that wouldn't be too tightly firewalled, so that requests would get promptly rejected (or handled if there is a trivial way of doing so), rather than timed out.

But, I'm looking for more specific advice of what works on practice.

(I'm familiar with other flavors of Unix/Linux, and TCP/IP in general, mainly from running applications on servers, but I don't have much experience on Ubuntu.)

These systems would be on Ethernet switch, but I don't think we can count on any router appliances.  I suppose one of the spare computers could be dedicated as a minimal router.

The objective of all this networking is to set up print sharing and perhaps file service, using one of the better computers as a server.

---

### Post by pirateghost on 2010-02-21
why not setup an old system with a router/firewall distro and restrict outbound access?

pfsense
vyatta
smoothwall
ipcop
endian

for ease of use i would go with pfsense, smoothwall, or ipcop.  this would give you a dhcp server, a gateway, and a way to prevent internet bound access.  all this could be easily configured through a webgui and not require you to do anything special.  you could even keep the WAN side of the firewall/router unplugged, but it would still leave you with dhcp, dns, gateway etc.

just a thought.

---

### Post by Charly85551 on 2010-02-23
Hi,
just an additional thought since I have set up a classroom with old PC's as well. Just used static addresses - say starting from 192.168.1.10 onwards to what ever is the required and have all connected to a switch. You can use a NAS-server or just a regular teacher's PC as your central storage system and just make sure they are made public to be viewed by the other PC's. You can always connect it to a router as *pirateghost* suggested but make sure that DHCP is switched off in the router and on the same address range (i.e. 192.168.1.1)or all your PC's are listening to the DHCP of the router.
cheers
charly

---

