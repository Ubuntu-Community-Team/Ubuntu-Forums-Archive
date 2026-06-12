---
title: "Random Sound Problem"
date: 2008-08-16
forum: Multimedia Software
---

### Post by mysterio2004173 on 2008-08-16
When I turn on my computer the sound works perfectly, but later on the sound just stops and I'm forced to reset my laptop. I followed the sound problem guide and this still happens. Please help.

---

### Post by mysterio2004173 on 2008-08-16
Please anyone know what to do?

---

### Post by cariboo on 2008-08-16
Give the following a try when your sound stops. In a terminal type:

```
alsa reload
```

This command reloads all the sound drivers.

Jim

---

### Post by mysterio2004173 on 2008-08-17
> **cariboo907 said:**
> Give the following a try when your sound stops. In a terminal type:

```
alsa reload
```

This command reloads all the sound drivers.

Jim

It said there were non to reload. But I compiled and installed my driver already.. weird..

---

### Post by cooke77 on 2008-08-17
Use Terminal...type lshw.
Find out what your Sound is (there).
And use that info...to look up 'relating info'...in Forum.

---

