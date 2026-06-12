---
title: "crosswire or ethernet"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by pavel989 on 2010-02-28
hey all. im trying to make an ubuntu server box my entrypoint to my networking. Meaning itll function as a server, a firewall, and a gateway. so i already installed dhcp3 and a dns server.

I have 2 ethernet cards in it. So now i wonder, should i the second card into a router's modem/wan port and make the router a switch? or should i plug it into one of the routers lan ports?

do i gain anything in the latter?

---

### Post by UrBob on 2010-03-01
Standard configuration would be to connect the Broadband Modem or Router to one network card, and the second network card connects to a (different) Router which supplies the rest of the network. With modern routers and broadband modems you should be able to use standard Ethernet cables, although some modems will auto detect for cross-over or straight through Ethernet.
 
If the router that connects to The Internet is also connected to the rest of your local network then you would bypass all control built into your server.
 
Hope this clarifies things.

---

### Post by pavel989 on 2010-03-01
> **UrBob said:**
> Standard configuration would be to connect the Broadband Modem or Router to one network card, and the second network card connects to a (different) Router which supplies the rest of the network. With modern routers and broadband modems you should be able to use standard Ethernet cables, although some modems will auto detect for cross-over or straight through Ethernet.
 
If the router that connects to The Internet is also connected to the rest of your local network then you would bypass all control built into your server.
 
Hope this clarifies things.

well my question is about the second card, in connecting to a different router, would i connect into the lan port, or a wan port

---

### Post by Iowan on 2010-03-02
Gut feeling is to consider your server the "WAN" and connect to the WAN port of the router - but I mis-guessed a similar setup with short-haul modems before...

---

