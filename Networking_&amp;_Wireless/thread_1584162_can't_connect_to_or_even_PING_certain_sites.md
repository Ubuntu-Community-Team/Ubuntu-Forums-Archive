---
title: "can't connect to or even PING certain sites"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by Todamont on 2010-09-28
Hi all. I've run into a problem I just can't figure out how to fix and was hoping someone else might be able to help. Running karmic, it seems my computer just CANNOT connect to certain websites sometimes, even though those sites are not down. I mean I cannot even ping the site. When I try to ping, the DNS routes just fine and I get the IP address with no problem, it just never gets any response. Trying to load the site in any browser just hangs and finally returns "unable to connect". 

Things I've tried:
disabling ipv6 via the about:config page (no effect)
adjusting MTU on my linksys router (no effect)
disabling tcp window scaling via /etc/sysctl.conf (no effect)
clearing browser cache (no effect)

"Down for everyone of just me" says dendroboard.com is up, and I can access it via my mobile phone. Etherape shows my computer sending packets to db1.dendroboard.com but not receiving anything back... So frustrating, and not the first time this has happened.

Anyone have any ideas? Please help?

---

### Post by blakep2 on 2010-09-28
Can you connect to the modem directly.  Also can other machines access the websites.

---

