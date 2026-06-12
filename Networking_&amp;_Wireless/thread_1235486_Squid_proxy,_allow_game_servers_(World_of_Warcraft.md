---
title: "Squid proxy, allow game servers (World of Warcraft, etcetc)"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by Josh1 on 2009-08-09
Hey all,

I've setup my home gateway machine to be a proxy server with squid, and basically it is setup like this:
((INTERNET)) <--PPPOE Cable Modem over Ethernet (Eth1)--> [[[SERVER]]] <-- (ETH0, DNS/DHCP/Squid basically internal network) --> SWITCH --> REST OF PC's

It's working perfectly, all the PCs have IP Addresses via DHCP, they all have Internet Access when setup properly in Firefox/IE (I have a proxy configuration URL in network settings to make things easier) and everyone can access the internet with no problems.

The only issue is that I can't figure out how to allow users on the network to play games online such as World of Warcraft, Warcraft 3, etcetc. I have a full port list, i've tried a few things with IPTables but I can't figure it out.

Should I switch to a transparent proxy? I'm not sure if this is what I want, as I read that SSL doesn't work over transparent proxies (as I need to access netbanking, which is SSL, tax office which is SSL, and countless other sites that support SSL).

Help would be appreciated as I am sitting here scratching my head and my family are starting to get a little annoyed that they can't play their MMO's. :P

---

### Post by green91 on 2009-08-09
Are you running NAT on the Server? IT should be sufficient for WOW.

---

### Post by Josh1 on 2009-08-09
> **green91 said:**
> Are you running NAT on the Server? IT should be sufficient for WOW.

Hmm.. I'll try. Will the users be able bypass squid? Or should I set it transparently?

---

