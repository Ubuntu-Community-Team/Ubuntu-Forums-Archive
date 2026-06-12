---
title: "eht0 not showing up after clean install of 12.04"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by larsdouglas on 2012-06-17
I installed 12.04 on a new machine two days ago. Everything went fine except that my network card isnt showing up in ifconfig.

ifconfig only show the loopback (lo)
But if I do lspci -nn I see the card (3Com ... Boomerang) so somewhere the system finds it. 
I guess its a driver problem, but the only driver I found that supports the Boomerang card is the xl-driver. But I cant figure out how to
* get it if it isnt on the system already
* activate it if it is on the system

In my desperation I tried 
sudo modprobe xl
but no banana.

Suggestions?

---

