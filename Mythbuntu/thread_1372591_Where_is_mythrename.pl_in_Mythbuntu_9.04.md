---
title: "Where is mythrename.pl in Mythbuntu 9.04"
date: 2010-01-04
forum: Mythbuntu
---

### Post by mekanix on 2010-01-04
Hi

Simple question - where is mythrename.pl located in Mythbuntu 9.04? I can't find it. 

Which package needs to be installed? I've tried all the location I've seen referred to here on Ubuntu-forums and on MythTV wiki.

I've tried "find" and it couldn't find it either.

Tried package.ubuntu.com - couldn't find any package with mythrename.pl for 9.04 (though it's there in 9.10).

- Bjarne

---

### Post by smartias on 2010-01-05
Hi Bjarne,

try ```
locate mythrename.pl
```. On my mythbuntu 9.04 it gave the following output:
```
/usr/local/bin/mythrename.pl
/usr/share/doc/mythtv-backend/contrib/mythrename.pl.gz

```

Hope, this helps.
Regards Matt

---

### Post by mekanix on 2010-01-10
Found the latter, thx!

- Bjarne

---

