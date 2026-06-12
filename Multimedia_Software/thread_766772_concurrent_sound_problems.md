---
title: "concurrent sound problems"
date: 2008-04-25
forum: Multimedia Software
---

### Post by cromestant on 2008-04-25
Im having some problems getting flash and rythmbox to work together, since I upgraded to hardy heron.. had no problems before, it seem sthat if one of the two is opened and playing asomehitng i have to reset both progs for the other one to work, or else it wont, i can t get the two to work together ( flash in firefox btw).

Now wierd thing is movie player does play nicely with flash, ...
i m not tied up to using rythmbox, so any suggestions would be heard..
thanks
charles

---

### Post by rotten777 on 2008-04-25
```
sudo apt-get install alsa-oss
```


I believe there was a genius decision to use a sound engine which by default isn't duplex. I could be wrong though. I'm trying to fix my own (same) issues right now by using ALSA.

---

### Post by rotten777 on 2008-04-25
dupe post. evidently the forums are having problems too....

---

