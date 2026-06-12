---
title: "Why is transmission telling me that basically all my ports are closed?"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by tegnoto89 on 2009-04-04
Transmission is saying that every port I check is closed; and transmission closes by itself after I try two or three different ones.  Also, canyouseeme is telling me that every port I've tried is closed.  What's going on here?

---

### Post by asuastrophysics on 2009-04-04
are you using the firewall tool ufw? if so, have you disabled any ports?

many unused ports are disabled by default. open unused ports are easily exploitable. 

what does "sudo ufw status" bring up in terminal?

---

### Post by tegnoto89 on 2009-04-04
"Firewall not loaded"

---

### Post by asuastrophysics on 2009-04-04
that eliminates ubuntu's firewall.  ;)

are you attached to a router? routers also act as firewalls. if you're connected to one, try bypassing the router and plug the ethernet cord straight into your dsl modem (assuming you have dsl)

do the ports open up?

---

### Post by WatchingThePain on 2009-04-04
I think ports are closed unless something is listening on them.
Ports can be opened manually for torrents if you need that.

---

