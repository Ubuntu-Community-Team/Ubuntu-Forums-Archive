---
title: "Huawei E353 Dongle only 3g"
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by mark6789 on 2012-07-05
I've got a E353 which is connecting in 3g mode, about .41Mbps, when I connect through windows the connection speed is 4Mbps through HSPA+.  Any thoughts?

---

### Post by Kirk Schnable on 2012-07-11
My thoughts...

0.41Mbps is awfully slow for 3G.  My 3G iPad gets 3Mbps through AT&T's network.

Before we can tell you if it's a driver related issue, we should be aware of which version of Ubuntu you're running.

It wouldn't hurt to tell us which kernel you're running as well.

You can get that information by running this in a terminal:
```
uname -r
```

In my efforts to Google for your issue's solution, I found a number of people talking about installing drivers for this card to get it working, but they're using Ubuntu 10.04, 11.04, etc.  Knowing which version you're running would help focus our efforts to help.

Kirk

---

