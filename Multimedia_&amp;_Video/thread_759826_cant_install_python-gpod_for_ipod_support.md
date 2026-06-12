---
title: "cant install python-gpod for ipod support"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by Annath on 2008-04-19
I need to install python-gpod to use this program I found to sync videos to my iPod. Amarok has no trouble with syncing music, but it doesnt do videos.  anyway, I go to synaptic to install python-gpod as told, and it says there is an unresolved dependancy, as it needs something else.
this is the error:

python-gpod:
  Depends: libgpod2 (=0.5.2-2) but 0.5.3+actually0.6.0-0.1 is to be installed

---

### Post by Annath on 2008-04-20
bump
 i know this isn't live support, but you can't help with something you can't see

---

### Post by dogeatery on 2008-06-02
Hey, I went looking all over and was in dependency hell, trying to make Exaile work with my iPod Shuffle.  Then I tried opening a terminal and it was simple:

```
sudo apt-get install python-gpod
```

Then restart your program and you should be good.

---

