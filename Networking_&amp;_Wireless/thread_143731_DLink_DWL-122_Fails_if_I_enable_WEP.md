---
title: "DLink DWL-122 Fails if I enable WEP"
date: 2006-03-13
forum: Networking &amp; Wireless
---

### Post by heislord5 on 2006-03-13
I have enternet if I do unsecured.  When I enable WEP, it won't connect.

The 10 digit key, do I enter it with or without the "s:"?  (Not that I haven't tried every imaginable combination 7 times each).

---

### Post by djroadrash on 2006-03-13
u have to put the s:
iwconfig [eth0 or whatever] essid [network name] mode managed key s:[password]

note that anything inside [] goes with no spaces and just one space after anything before []

also can put all this in system/admin/networking
look for your wireless card  and sellect it, configure (put all info there) and start on.
good luck:-D

---

