---
title: "Quod Libet:"
date: 2008-12-15
forum: Multimedia Software
---

### Post by Ubuntist on 2008-12-15
I've installed Quod Libet 2.0 using

```
 apt-get install quodlibet quodlibet-ext quodlibet-plugins
```Unfortunately, when I try to run it, I get the following error:
```
Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 19, in <module>
    import config
ImportError: No module named config

```Where do I go from here?

By the way, does anybody know what *quod libet* means?  My Latin's none to good.

---

### Post by kpkeerthi on 2008-12-15
> **Ubuntist said:**
> I've installed Quod Libet 2.0 using

```
 apt-get **[COLOR="Red"]remove[/COLOR]** quodlibet quodlibet-ext quodlibet-plugins
```

You installed it with apt-get **remove** ?

---

### Post by Ubuntist on 2008-12-15
> **kpkeerthi said:**
> You installed it with apt-get **remove** ?

Uh, no.  [IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG]  That would have been quite a trick!  I used *install, *not *remove.*

---

