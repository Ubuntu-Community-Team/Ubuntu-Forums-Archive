---
title: "Level1 WPC-0301 Wifi pc-card"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by b0bby on 2006-07-07
Hello =)

I had a Level1 WPC-0301 rev2 wifi pccard, witch was working perfectly with Dapper Drake, so I bought another one today ( i have two laptops ) but it was  rev3, and its not working very good, i find my accesspoint, and it has perfect quality on the connection but when i try to connect it only says failed, the old, rev2, card works without a problem on both my computer, and the new one gives the same error on both computers :(

Anyone got an idea how i fix this?

---

### Post by tturrisi on 2006-07-08
The newer levelone likely has a different chipset:
[http://linux-wless.passys.nl/query_part.php?brandname=LevelOne](http://linux-wless.passys.nl/query_part.php?brandname=LevelOne)

---

### Post by b0bby on 2006-07-10
ah, yes, why didn't i think of that :/
Is there anyway to get info about the chipset? w/o removing the cover of the card.

---

### Post by tturrisi on 2006-07-10
I suspect that version 2 was upgraded to version 3 to support 128 bit encryption.  The level1 site has zips for windows drivers (12 mb) and version 2 & 3 are the same driver, so likely is same chipset.. See if there's a changelog in the zip that explains the revisions.  What driver is ubuntu loading for this card?

---

