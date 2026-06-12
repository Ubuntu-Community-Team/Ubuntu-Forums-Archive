---
title: "Broadcom wireless card question"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by slammed87d21 on 2009-01-25
Well, I have a Broadcom BCM4311KFBG wireless card laying around. What I was wondering was is it better, worse, or about the same as the AR242x 802.11abg wireless cards I have in my Acer Spire One and 4720Z? Also, if it is better, what do I need to do software wise to use it?

---

### Post by diablo75 on 2009-01-25
The best way to find out is to probably test it yourself.  I've never really noticed a bit of difference when comparing performance between two different cards.  Only thing I think I'd pay attention to is it's reception abilities.  The more, the better (of course).  And of course whether or not either card is capable of working "out of the box" without any need to install proprietary drivers is also something I look out for.  Personally, I prefer my D-Link WNA-2330.

---

### Post by slammed87d21 on 2009-01-25
So what's the best way to set up the Broadcom card? All I've ever used is Atheros cards, so I have no clue...

---

### Post by kevdog on 2009-01-25
I want you to take a look at this page.  It gives you a lot of background and possible options.  I have a 4306 and am using the b43 driver.  4311 can use b43, the broadcom STA driver (AKA wl), and ndiswrapper (which I don't recommend).  Pick between the b43 or wl driver (or choose both and try both to see which one gives you better performance).  

[http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61](http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61)

---

### Post by slammed87d21 on 2009-01-25
thanks

---

### Post by slammed87d21 on 2009-01-25
Tried the Broadcom card in both my Aspire One and Aspire 4720Z. Works 10 times better than the Atheros card.

---

### Post by kevdog on 2009-01-26
Atheros is going through some changes right now, but I own both a Broadcom and Atheros.  I really can't tell the difference between the two.  I'm able to do Monitor Mode with the Atheros -- never tried with the Broadcom.

---

