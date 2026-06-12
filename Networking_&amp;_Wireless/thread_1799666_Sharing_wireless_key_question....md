---
title: "Sharing wireless key question..."
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by j*tech on 2011-07-07
Im using WPA with a TKIP pre-shared key...Can a client pc im sharing my key with access my files if im not file sharing?  Router config?

---

### Post by Dangertux on 2011-07-08
In theory yes to both questions --

Realistically the only one that would be relatively easy is the router config, since all they would have to do is know the password, figure out the password, sniff the password (most low end SOHO routers don't use SSL to login), bypass the login alltogether, and or a number of other methods for taking over the router.

In theory if you're not sharing files but have any other service running that service could be exploited in order to either gain a remote shell, and allow the attacker access to your files and whatever services they wanted to start.

Realistically, unless the person you're sharing the key with hates you, gives it to someone else, or spends alot of time noodling in things just to tick people off. Not likely.

---

### Post by j*tech on 2011-07-11
They are complete tech noobs lol and it doesn't sound like an easy task (even for a determined attacker)...I have a strong router password and wifi settings, UFW, file sharing off, and a strong login password, so sounds like im alright...the best offense is a good defense :biggrin:...

---

