---
title: "a strange issue with wireless"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by JaysonLean on 2010-01-04
Hej, folks, got a strange prob with network manager. Actually, I use wireless in 2 places - at work and at home. The thing is that my wifi module stopped (it did work before) to see any networks at home, but at work its still fine. I guess this all happened after I switched wireless button on my laptop couple of times when device attempted to connect to a nearby network.
After I tryed to reload wireless list by both

iwlist wlan0 scan

and 

watch -n 1 "iwlist wlan0 scanning"

it just said 

wlan0     Failed to read scan data : Resource temporarily unavailable.

As above, problem persists only at home.
So may be should I somehow reinstall network manager or roll back to initial settings, and if yes - how would I do this? Thanks so lot if anyone knows how to figure out of this.

---

