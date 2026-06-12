---
title: "How i can use &quot;wireless modem&quot;, wlan, lan (eth0) at the same time?"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by natanael.id on 2009-09-18
Dear all,

i have computer with wireless modem, wlan, and lan card, when i activate wireless modem for internet connection then i activate wlan for local network connection, i can not run my internet. please help me to resolve this problem, thanks.

---

### Post by t0mppa on 2009-09-19
Sounds like a case of mistaken identity, where your system is trying to route traffic outside your local network (ie. to Internet) through the wlan card, while it should be using the modem for that and the card only for local network.

Just to be sure though, open up a terminal (when both of the wireless devices are in use), run **route** and post back with the results.

---

### Post by i.r.id10t on 2009-09-19
Change that route to route -n

But yes, this sounds like a routing issue.

---

