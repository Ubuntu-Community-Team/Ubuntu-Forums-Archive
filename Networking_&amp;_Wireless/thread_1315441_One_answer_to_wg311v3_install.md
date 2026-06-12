---
title: "One answer to wg311v3 install"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by dvdljns on 2009-11-05
Trying to get wg311v3 to work it would setup with out any errors but I would have no wireless ext. in ubuntu. In fc3 it would connect to the router give me an ip but would only connect at 1 or 2 b/s Not enough to surf the web. giving up and trying to conect with another wireless card it started working as wlan2. Doing some expermenting here is what seems to be happening. when you do ndiswrapper -m it writes wlan0 for modprobe but for whatever reason the card will not work setup as wlan0. if you change the 0 to another # [ I tried 1 through 5] it works. I checked it on both fc3 and ubuntu hardy on 6 computors with the same results. Do not know what caused it but the problem is consistant with this card. I thought users where crazy when they posted that the card worked out of the box with ndiswrapper.
Thought this info might help someone else.

---

### Post by Skripka on 2009-11-05
My WG311v3 worked out of the box with Ndiswrapper under 8.04, and 8.10 using wlan0

---

### Post by dvdljns on 2009-11-05
> **Skripka said:**
> My WG311v3 worked out of the box with Ndiswrapper under 8.04, and 8.10 using wlan0
I think most do. but if someone has one that does not seem to work any other way maybe it is from the same batch as mine. don't know, it is weird but it is working but won't if I change it to wlan0. never heard of that before.

---

