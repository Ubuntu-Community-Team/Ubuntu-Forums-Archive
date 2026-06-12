---
title: "nero cd-dvd speed"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by newman on 2007-09-26
Is there a linux equivalent for testing the burn quality of DVDs?

---

### Post by newman on 2007-09-29
I haven't found anything yet.
Anyone?

---

### Post by Parallel on 2007-09-30
[http://qpxtool.sourceforge.net/](http://qpxtool.sourceforge.net/) perhaps?

---

### Post by blue212 on 2007-11-08
qpxtool works well, its lets you do media check, transfer rates, pi/cx, jitter/beta, FE/TE, TA.

Although, if you don't have a compatible DVD drive you might not get many features... check their website

Plus they have a plextor firmware that unlocks some advanced burning features. It revived my plextor px-760a which would not burn properly in WinXP 

```
sudo apt-get install qpxtool
```

```
sudo apt-get install pxfw
``` (for the plextor firmware updater)

---

