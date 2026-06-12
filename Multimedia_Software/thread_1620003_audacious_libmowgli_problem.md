---
title: "audacious libmowgli problem"
date: 2010-11-12
forum: Multimedia Software
---

### Post by meliniak on 2010-11-12
Salutations,

I've been struggling with getting audacious working for the past hour. I'm using synaptic to install it. When trying to run it from the bash, I'm getting the following error:


```
audacious: error while loading shared libraries: libmowgli.so.1: cannot open shared object file: No such file or directory

```

I tried to make /usr/lib/libmowgli.so->libmowgli.so.1 link, but it didn't help. Tried reinstalling audacious/libmowgli and a few others packages, but in vain, too.

Could you guys share any hints that might track down the problem?

---

### Post by meliniak on 2010-11-28
Anybody? Any ideas? :roll:

---

### Post by Yellow Pasque on 2010-11-28
You made the link go the wrong way. ;)

And maybe you want to just purge libmowgli1 and reinstall it.

---

