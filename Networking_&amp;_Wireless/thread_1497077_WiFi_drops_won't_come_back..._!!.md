---
title: "WiFi drops won't come back... !!"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by KaYnemO on 2010-05-30
I have just upgraded to Lucid Lynx and my WiFi drops out of the blue and won't return, unless I manually turn it off with a button and then turn it back on. my controller is Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection . The notebook is Acer Aspire 5670,  I tried to google around but didn't find any particular suggestions, anyone knows how to fix the problem?

SOLUTION:

Just stumbled on this and it seems to work:

sudo apt-get install linux-backports-modules-wireless-2.6.32-22-generic

seems to do the trick.

---

