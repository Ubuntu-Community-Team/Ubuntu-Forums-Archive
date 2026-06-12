---
title: "syslog overwhelmed by DoRxHighPower"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by desconocido on 2009-08-12
Since some semi-automatic security upgrade of Hardy, my syslog (and some other logs) is overwhelmed by messages of the type

```
Aug 12 11:46:51 faustino kernel: [ 1330.168808] DoRxHighPower(): RF_ZEBRA, Upper Threshold: 99 LOWER Threshold: 70

```

My problem is that my logs have become unusable - they don't stay still long enough for me to read them.

Apparently this has gone away in Intrepid or Jaunty, but I don't want to change from Hardy yet. Is there an individual patch, maybe in some kernel or networking library that I could apply just to get rid of this?


Thanks

---

### Post by SolarOnline on 2009-08-12
[Kiwi Syslog Server v9]("http://tinyurl.com/pd3dv8") should be useful in helping you here. 

Especially the log archiving which will help with the problem of logs not staying long enough to read them.

---

### Post by desconocido on 2010-07-24
In the end I just selected everything in the log, copied it and pasted into gedit.

I'm using Karmic now which does not have the problem.

---

