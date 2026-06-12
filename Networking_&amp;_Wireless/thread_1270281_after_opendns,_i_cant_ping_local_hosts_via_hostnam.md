---
title: "after opendns, i cant ping local hosts via hostname"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by puccaso on 2009-09-19
yea so i use opendns, otherwise i get no wordpress or youtube. i live in turkey at the moment..

ne way - 

how do i set up my network, so that all remote calls use opendns servers
but local ones, on the same subnet can talk to each other directly?

i know i have to use avahi somehow, 

if i dont use the opendns servers, and use my routers dns,
i can ping via .local suffixes but right now i cant



i have two systems

192.168.2.21 puccaso-lp 
192.168.2.22 puccaso-lp-nix

---

### Post by Brandon Williams on 2009-09-19
My router allows me to specify the external DNS servers that it uses. I could specify the opendns servers, for example. This would allow me to continue using my router for local DNS and know that it was getting answers from opendns for other things. Is this a configuration supported by your router, too?

If not, then you might have to add entries to your /etc/hosts files on the individual machines, or run a dns server on one of your local machines that splits requests correctly between the router's dns and opendns based on the domain.

---

### Post by Iowan on 2009-09-20
I've set up DNSMasq to act as DHCP/DNS on my network (still polishing some details). It has an option to serve address to the local network - and can be set wo it doesn't forward (out of network) requests for hosts without a suffix.

---

### Post by puccaso on 2009-09-20
yea but these are two laptops
can i have dnsmasq working on two clients without software?

---

