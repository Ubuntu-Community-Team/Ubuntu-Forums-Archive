---
title: "Error Ati: libGL warning: 3D driver claims to not support visual 0x4b"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by WhizCas on 2006-10-24
Hi,

when running programs using 3D im getting this error.

> $ glxgears
libGL warning: 3D driver claims to not support visual 0x4b


Anybody knows what's causing this error?

---

### Post by sp4rd on 2006-10-24
That's just a warning telling you that the driver doesn't support  that color depth, which in this case 32 planes=0x4b.
```
glxinfo -i |grep -i "0x4b" 
```
or 
```
xdpyinfo
```
at a console will show more info.  Don't think it's much to worry about.  Does glxgears not work for you after you get this warning?

---

### Post by WhizCas on 2006-10-25
Yes glxgears runs smooth...

Also programs do work, but im really curious why im getting this error...

---

### Post by hikaricore on 2006-10-27
Same error here except I can't get glxgears to run or anything that uses the mesa driver.  Worked fine before the upgrade on this comp. :/

---

### Post by WhizCas on 2006-11-01
Well GlxGears works fine here

---

