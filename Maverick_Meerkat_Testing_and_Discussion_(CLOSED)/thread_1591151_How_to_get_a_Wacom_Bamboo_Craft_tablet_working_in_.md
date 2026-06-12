---
title: "How to get a Wacom Bamboo Craft tablet working in Ubuntu 10.10?"
date: 2010-10-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by TheNerdAL on 2010-10-08
So I had it working in 10.04 but now it doesn't work quite well. How can I fix this? :( 

Thanks.

---

### Post by Favux on 2010-10-08
Hi again TheNerdAL,

All I had to do was compile linuxwacom to get a newer wacom.ko.  See part I. at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by TheNerdAL on 2010-10-09
> **Favux said:**
> Hi again TheNerdAL,

All I had to do was compile linuxwacom to get a newer wacom.ko.  See part I. at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

I did that and I get the same problem when I use the tablet with my finger. It doesn't work smoothly.

---

### Post by robert shearer on 2010-10-09
On this How-to...
[http://ohioloco.ubuntuforums.org/showthread.php?t=1515562](http://ohioloco.ubuntuforums.org/showthread.php?t=1515562)

scroll to...
> Attention those who have been having problems with touch and gestures. See post #110 or Troubleshooting below for a fix.

for the fix.

---

### Post by TheNerdAL on 2010-10-09
> **robert shearer said:**
> On this How-to...
[http://ohioloco.ubuntuforums.org/showthread.php?t=1515562](http://ohioloco.ubuntuforums.org/showthread.php?t=1515562)

scroll to...


for the fix.

I don't see ```
#define BAMBOO_TOUCH_JUMPED 30

``` at line #34 or so.

---

