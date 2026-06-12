---
title: "wlan"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by dinhunzvi on 2012-04-25
i recently bought a RealTL8188CU wireless lan adapter. it works perfectly in Windows but in Ubuntu Linux it detects the network but does not connect. what could be the problem

---

### Post by lz1dsb on 2012-04-26
> **dinhunzvi said:**
> it detects the network but does not connect. what could be the problem
What do you mean by that? Do you mean that the network card is recognized? Can you configure a static IP address and communicate within your network?

---

### Post by dinhunzvi on 2012-04-26
the card can detect the available wireless networks but it can't connect to anyone of the,

---

### Post by lz1dsb on 2012-04-27
Do you see any logging messages in /var/log/demesg file? It should provide information on what's going on while your laptop is trying to associate with the AP...

---

