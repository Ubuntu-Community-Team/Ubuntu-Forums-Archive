---
title: "Crackly Sound w/Certain Apps"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by z00s on 2007-03-18
I'm using a Sound Blaster Audigy and with the following apps I get sound that crackles. Every other program works fine:

neverball
neverputt
scorched3d
zsnes
lincity-ng

Every volume setting in alsamixer is off except for Analog F. Does anyone have any thoughts as to what could be going on here?

---

### Post by z00s on 2007-03-19
mmmm bueller?

---

### Post by laberer on 2007-03-30
I had the same problem with the same apps.

Installing **libsdl1.2debian-oss** instead of **libsdl1.2debian-all** solved the crackle.

---

### Post by kidcharles on 2008-02-02
I was able to stop crackle sounds while running Globulation 2 by installing libsdl1.2debian-oss as well, thank you very much for this fix!

---

