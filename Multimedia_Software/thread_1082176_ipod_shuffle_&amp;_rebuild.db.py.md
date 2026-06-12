---
title: "ipod shuffle &amp; rebuild.db.py"
date: 2009-02-27
forum: Multimedia Software
---

### Post by jeamer on 2009-02-27
Hey, I inherited a shuffle (no way would I buy an apple product) and have been doing just fine using rebuild.db.py and nautilus. However, I would love to be able to order my songs correctly so if I turn off the shuffle feature (because wow, doesn't the ipod shuffle have so many "features", totally worth 60 bucks :roll: ) my songs will play in order. I have the albums organized into their respective folders. I've read somewhere that the database rebuilder orders songs alphabetically, but there is no way to tell (the log doesn't mention anything about song order). Thanks in advance!

---

### Post by kalos on 2009-09-20
From their [website]("http://shuffle-db.sourceforge.net/") it sounds like it orders alphabetically by default. (See "Sorted filenames (new-school)")

The code certainly seems to sort.
```
  files.sort(cmp_key)
```

Is it not working for you?

---

### Post by jeamer on 2009-10-17
Hey yeah, just came across this by chance. Old thread. Yes you're right, it is sorted alphabetically, and you have to pay attention to file structure as well, as folders can cause issues. Short answer, yes, alphabetical. Thanks.

---

