---
title: "Gimped WRT54GS Linksys Connection"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by BJ_Covert_Action on 2009-03-09
Hey All,

So I've been noticing some crapped out internet speeds on my linux box which led me to do some digging on my router (WRT54GS v5.0) thinking that I might be able to optimize it to produce faster DSL speeds. However, when I checked my connection speed I noticed that I am only getting 1-2 Mb/s across my wireless connection to it. I hadn't noticed this before, just attributing slow net speeds to a crappy DSL connection. Anyways, this led me to look into my roomate's laptop which is also connected wirelessly to the internet through the same router. It is getting the full 54 Mb/s and is running Windows XP.

So basically, I am trying to figure out why my Ubuntu box (version 8.04) would have a gimped connection to it. I logged into my router and found some of the settings on it which are listed below. Can anyone give me any hints or pointers as to why Ubuntu would be having problems gaining full connectivity though?

Setup:
DSL internet cable from phone jack in wall --> DSL Modem
DSL modem ethernet cabled to WRT54G v5.0 router
Router firmware: Linksys firmware version 1.50.9

Router Settings:
DHCP Server Enable
Maximum number of DHCP clients allowed: 5
No static DNS or WINS addresses specified
MTU: Auto
Default starting IP address and subnet mask
DDNS: Disabled
MAC Address Clone: Disabled
Operating Mode: Gateway
Interface: LAN and Wireless
Wirless Network Mode: Mixed
Wireless Channel: 6
SSID: Enabled
WEP Encryption: Enabled
MAC Filter Disabled
Block Anonymous Internet Requests: Enabled
Filter Multicast: Enabled
Filter IDENT: Enabled
IPSEC, PPTP, L2TP Passthrough Enabled

And that's about it for details. Any ideas on what might be going on with my Ubuntu connection? Let me know and thanks in advance.

As a caveat, I don't know a whole helluva lot about networking other than how to plug the cables in correctly and login to the router, so any other tips on configuration or resources for learning would be much appreciated.

Cheers,
Brady

---

