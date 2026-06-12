---
title: "installing wireless router - how?"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by nagaraj on 2009-04-18
hi,
i am trying to install a 'belkin wireless G router' on my 8.04 pc so that i can use my laptop ( wireless ly) through the same modem. the connections i made are comp>wireless router>adsl modem (always on internet connection from isp - bsnl). firefox shows 'connection error'. what might be the problem? all proper lights are glowing.

---

### Post by Trafficflow on 2009-04-18
The modem goes in front of the router

---

### Post by Ericyzfr1 on 2009-04-18
> **nagaraj said:**
> hi,
i am trying to install a 'belkin wireless G router' on my 8.04 pc so that i can use my laptop ( wireless ly) through the same modem. the connections i made are comp>wireless router>adsl modem (always on internet connection from isp - bsnl). firefox shows 'connection error'. what might be the problem? all proper lights are glowing.

Can you see your wireless network? Are you able to connect through wired network?

---

### Post by nagaraj on 2009-04-19
if i eliminate the router and connect my desktop directly to the modem then i can connect to the internet - start and stop modem by commands ' sudo pon dsl-provider' and sudo poff dsl-provider' resp. the router installation instructions are for windows and the connections are as mentioned in the manual. modem cannot be connected between router and pc. this router can take upto 4 wired connections and 28 wireless connections. i am trying to connect my desktop pc through wired connection as detailed in my original query. i have a windows laptop i want to connect wirelessly.

---

### Post by nagaraj on 2009-04-19
thanks all, i could finally install the wireless router. the belkin user manual gave an alternate setup method. the key is to change the network settings from 'roaming mode' to DHCP. then it starts detecting the router as DHCP. rest all is done by using the belkin online setup programme.
thanks anyway

problem solved.

---

