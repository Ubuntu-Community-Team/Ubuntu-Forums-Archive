---
title: "Everything works except Pokerstars(wine)"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ToxinPowe on 2010-09-07
Like the title says, I have all working now on Maverick, but my client of pokerstars(wine) doesn't works, no errors. Any clue please?

Thanks.

---

### Post by lamb123 on 2010-09-16
Same here, and Full Tilt Poker does not connect either. Looks like connection is blocked for wine apps?

---

### Post by OneWhoShanks on 2010-09-16
[http://appdb.winehq.org/appview.php?iVersionId=2899]("http://appdb.winehq.org/appview.php?iVersionId=2899")

> Under kernel 2.6.35 using Ubuntu Maverick 10.10 and wine 1.3.2, here's one more way of making it work. This is probably the easiest:

setcap all=eip /usr/bin/wineserver
setcap all=eip /usr/bin/wine-preloader

This gets around the security stuff and is almost equivalent to running it as root. You could probably get away with a smaller set of capabilities than "all" but someone would have to know more about wine debugging than me to figure out which are the specific capabilities that keep PokerStars from making its connection.

Weirdly "Network Status" still doesn't work even though you can install other windows network debug tools like WinPcap and they are capable of ICMP (ping).


credits to michael at winehq

---

### Post by Quackers on 2010-09-24
Thank you OneWhoShanks (don't we all?) I can now play poker again :-)
The terminal didn't like setcap though. I had to install some lib thing first.

---

### Post by Quackers on 2010-09-24
Dodgy double post.

---

### Post by newbiefly on 2010-10-10
Thank you OneWhoShanks and michael at winehq.  Much love.

---

