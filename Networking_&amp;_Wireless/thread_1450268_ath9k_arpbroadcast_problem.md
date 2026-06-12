---
title: "ath9k arp/broadcast problem"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by fpereira76 on 2010-04-08
Hi all,

I have an Acer notebook with ath9k chipset wireless interface, which neither responds to arp "who-is" messages, nor accepts any broadcast messages or incoming connections. For that reason, I cannot connect to the laptop from any other PC in my LAN.

Arp/broadcast messages and incoming connections are normally accepted when the interface is in "promiscuous" mode. They are also accepted after the laptop establishes an outgoing connection to any other PC in the LAN.

It seems that the problem is due to the fact that ath9k driver is rejecting the "who is" arp messages. However, I do not know how to circumvent this.

Thanks for any help.

F.

---

