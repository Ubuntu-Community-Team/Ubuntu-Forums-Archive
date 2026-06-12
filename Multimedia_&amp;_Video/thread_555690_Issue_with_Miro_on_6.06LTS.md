---
title: "Issue with Miro on 6.06LTS"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by stevex on 2007-09-20
So I decided to finally try Miro and I added the Miro repository for Dapper to apt and downloaded the program.  The issue is when I attempt to load the program, I appear to possible have some kind of environment problem that if keeping Miro from starting. 

```
steve@sarah:~$ miro
Traceback (most recent call last):
  File "/usr/bin/miro", line 25, in ?
    gtcache.init()
  File "/usr/lib/python2.4/site-packages/miro/gtcache.py", line 17, in init
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
```

I am not sure how I could go about fixing that, any idea?

---

### Post by yadayada2 on 2008-05-09
I have the same problem with 8.04 and miro. :(

---

