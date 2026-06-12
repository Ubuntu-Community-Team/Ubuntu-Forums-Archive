---
title: "Which Mini PCI-e Half wireless card works with N"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by rurodrig on 2012-06-08
So i bought an intel centrino n1000 so I could get on my faster N wireless band, only to find out the drivers available for linux aren't compatible with N.

So does anyone know which mini pci-e half wireless card works best with N in Ubuntu?  Preferably with native drivers.

---

### Post by rurodrig on 2012-06-08
Well I think I figured out the answer.

Went here:

[http://en.wikipedia.org/wiki/Comparison_of_open_source_wireless_drivers#Linux](http://en.wikipedia.org/wiki/Comparison_of_open_source_wireless_drivers#Linux)

And saw that the only linux drivers that do 802.11n are ath9k (atheros) and iwlagn (intel).  Since I had a bad experience with my first intel wireless, I decided to go with an Atheros AR9285.

---

### Post by rurodrig on 2012-06-15
So I got the Atheros, put it in, and same story as my intel centrino.  Doesn't see the n band.   What gives?  Anyone have any clues?

---

### Post by rurodrig on 2012-07-15
After some research, I found out the Atheros does N, but not 5 GHz.  My router does N on 5GHz.

So I finally found a card that does N, on 5 GHz.  It's the intel ultimate N 5300.  Maybe it's just the wifi driver finally got N support or something, but it worked right out of the box.

Problem solved.

---

