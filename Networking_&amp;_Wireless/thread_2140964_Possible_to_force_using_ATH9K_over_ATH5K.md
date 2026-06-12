---
title: "Possible to force using ATH9K over ATH5K?"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by GarEngLLC on 2013-05-01
I have a wireless card that comes up and works fine in Ubuntu 12.04 and uses the ATH5K driver.  What I want to do is try to force it to use the ATH9K driver instead since I cannot seem to get it to force a data rate using the current driver (```
sudo iwconfig wlan0 rate 1M
``` doesn't seem to have any effect with the ATH5K on my system).  

Any tips for making that happen smoothly?

---

### Post by wildmanne39 on 2013-05-01
You can not force it to use the ath9k driver at least not without rewriting the driver.

---

### Post by GarEngLLC on 2013-05-01
Shucks!  OK, thanks.  Guess I am back to figuring out why I can't set the rate with the ATH5K. Thanks.

---

