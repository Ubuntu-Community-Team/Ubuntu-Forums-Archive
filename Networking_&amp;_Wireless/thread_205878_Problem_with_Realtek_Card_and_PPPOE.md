---
title: "Problem with Realtek Card and PPPOE"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by Indrek on 2006-06-29
My friend has installed Ubuntu :). But He can't get pppoe, pppoeconf is not working (it say's, it wasnt found anything). We have tried dns too, no diffrence. Then the last thing what I think is Realtek Intregated Network card. Beacause my VIA one is working fine, but in windows he must connect his pppoe with special program. But I just connect with windows gui and it works.

Any Ideas?

---

### Post by xbadger on 2007-02-12
try:
sudo ifdown eth0
sudo ifup eth0
sudo pppoeconf

---

