---
title: "dsl over wireless"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Hakimjo on 2009-11-14
I'd like to establish a dsl (pppoe) connection via a wireless link to my "modem".  Network manager does not allow for pppoe in the wireless tab, nor for wireless in the dsl tab.  How to solve this problem ?

Thanks

---

### Post by driftertx on 2009-11-14
uhm, as far as I know your modem from your carrier (ATT/Verizon etc.) won't support that over wireless... The easier way to do this is go buy a 30-40$ router (linksys or other brand) to establish the PPPoE connection through the wired port and then wirelessly connect to the linksys or other brand access point. If you went the route of establishing the PPPoE connection with just your one PC no other computer can use the connection...

---

### Post by Hakimjo on 2009-11-14
> **driftertx said:**
> uhm, as far as I know your modem from your carrier (ATT/Verizon etc.) won't support that over wireless...

No problem with the provider's modem ... the dsl over wireless connection works fine from my OSX machine.

---

### Post by driftertx on 2009-11-14
Alright, well, your best bet is to buy the cheap wireless router to plug into the carrier's modem and bypass making the PPPoE connection from your computer and make it from that wireless router. Come to think of it, ATT routers can be modified to do the PPPoE establishment and not just bridge your connection BUT you need to know your username/password for your account though and know how to access the modem's interface. They may be able to walk you through this.

I'm not sure of your network knowledge so unless you know what you're doing I wouldn't go that route. My 'buy a cheap wifi router'  would solve your problem and also allow any computer in your house to use the connection without having to establish PPPoE and would just need the wireless connection. If you don't like that solution you'll have to wait for someone to chime in on how to troubleshoot PPPoE connections.

---

### Post by perskepit on 2010-07-08
I see this thread is pretty old but I have been sitting with the same issue.  The way I solved it was to connect to the wireless router and then run pppoeconf to establish the pppoe connection.  I am using a provider specific modem and it works like a charm.

---

