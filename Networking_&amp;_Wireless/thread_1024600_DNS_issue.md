---
title: "DNS issue"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Josep CA on 2008-12-29
Hi,
I'm quite noob using Ubuntu and since I upgraded from 8.04 to 8.10 I'm unable to load ubuntu (loading stops in "running local boot scripts (/etc/rc.local)). I've tried apt-get update but it seems there is a DNS problem, nslookup and dig show "connection timed out; no server could be reached". I have a working ADSL connexion in my laptop (it works in the same machine where I have xp installed in another partition).
Any help will be welcomed.

---

### Post by fx78 on 2008-12-29
Can you give us some more background information ? Is the ADSL modem connected directly to your computer ? Or is there a router in between ?

Can you ping google (without dns)? Try

> ping 64.233.183.104

---

### Post by Josep CA on 2008-12-29
> Is the ADSL modem connected directly to your computer ? Or is there a router in between ?

I have ADSL modem connected directly to my computer.

> Can you ping google (without dns)?

When I try ping 64.233.183.104  I get "Network is unreacheable"

---

### Post by fx78 on 2008-12-29
Could you give the brand and type of the modem ?

Any idea how the ADSL modem was setup in windows ? If you need a login and pass to setup the link then you will need to do the same in ubuntu.

Try checking your network connections in xp and see if any PPPOE connection is listed, if so you'll probaly need to setup a PPPOE connection in ubuntu.

---

### Post by Josep CA on 2008-12-29
My connection worked with Ubuntu 8.04 without any need to configurate nothing.
My modem is P660R D1 RoHS

---

### Post by fx78 on 2008-12-29
Ok found out that it's a zyxel P660R modem/router. So no setup required. Sounds like a DHCP problem
Any chance you could attach your /var/log/messages and /var/log/syslog file ?

---

