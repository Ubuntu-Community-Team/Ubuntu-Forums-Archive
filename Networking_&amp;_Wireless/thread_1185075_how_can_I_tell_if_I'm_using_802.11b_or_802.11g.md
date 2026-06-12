---
title: "how can I tell if I'm using 802.11b or 802.11g?"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by negativ on 2009-06-11
Problem is this:  I am sitting about 10 feet away from my wireless router.  There are no other APs using the same channel I'm using.  Yet, transferring a file from my desktop (wired) to my laptop (wireless) is trucking along at approximately 5-6mb/s.  The card in the laptop supports 802.11g, as does the router, and I understand that real-world throughput for 802.11g is something like 20mb/s.  Yes, I know the difference between megabits and megabytes.

I am trying to figure out if my card (ipw2200) is falling back to 802.11b, or if I have some other problem, or if this is really as good as it gets.  I've never really transferred large ( >200MB) files over a wifi lan before, so maybe I'm expecting too much.

Any help would be appreciated.

---

### Post by negativ on 2009-06-11
obviously, "cow" in the subject line should be "how".

/facepalm++

lol @ self

---

### Post by dmizer on 2009-06-11
> **negativ said:**
> obviously, "cow" in the subject line should be "how".

/facepalm++

lol @ self

Fixed :)

Take a look at the output of either:
```
ifconfig
```
or
```
iwconfig
```

---

