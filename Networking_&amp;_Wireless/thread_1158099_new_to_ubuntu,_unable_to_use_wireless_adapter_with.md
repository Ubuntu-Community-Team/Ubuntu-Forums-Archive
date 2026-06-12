---
title: "new to ubuntu, unable to use wireless adapter with it."
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by mikeds123 on 2009-05-13
im new to ubuntu, although i have kubuntu, i was told they were almost the same.

i have a netgeat WG111T wireless adaptor, however, when plugged in and kubuntu is in use, it fails to work, i have tried the instalation CD, but it just asks me what programme i would like to run it with, and whenever i try it with dolphin or konquerer, the same pop up appears again....I run it duel with win vista, which although im unsure may be the problem, it could be at the same time.

if any body can shed some light onto how im able to sort this and connect to the internet please tell :D thanks

---

### Post by superprash2003 on 2009-05-13
post output of **lshw -C network** from the terminal

---

### Post by mikeds123 on 2009-05-13
care to explain that in simpler terms, as i said im new xD lol sorry

---

### Post by uupreti on 2009-05-13
> **mikeds123 said:**
> care to explain that in simpler terms, as i said im new xD lol sorry

Go to **terminal** by  pressing **ALT-F2** and enter **konsole** and hit enter. Then give the output of following commands. 
[B]1. lshw -C network 
2. ifconfig 
3. iwconfig 
4. iwlist scan [/B]

---

### Post by mikeds123 on 2009-05-13
thanks very much :)

---

