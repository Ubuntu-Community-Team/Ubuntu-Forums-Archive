---
title: "Acidrip can't find DVD"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Hribar74 on 2009-12-07
Hi,
I'm trying to rip some DVD's so I don't have to lug them with me on a trip next week, but AcidRip can't find the DVD drive.  I've tried ```
/dev/dvd (The default at startup)
``` and ```
/dev/dvd/VIDEO_TS
``` among others and it tells me that those locations don't exist.  How do I get it to find the DVD?  Am I just putting in the wrong locations and how do I find the right ones?

HALP!!!:confused:

---

### Post by lavinog on 2009-12-07
I recall a bug with some dvd rippers not accessing the correct device.
run acidrip in a terminal and see what error it gives.
if it says something like /dev/dvd not found, check that /dev/dvd exists...on my system I have a /dev/dvd1 but not a /dev/dvd  I think it was this change that broke the rippers.

if this is the case you can create a temp symlink:
```

sudo ln -s /dev/dvd1 /dev/dvd

```

---

