---
title: "Help reading bad DVD"
date: 2008-06-03
forum: Multimedia Software
---

### Post by jcrpereira on 2008-06-03
Hi, i have a dvd camcorder and it sometimes fails to properly finalize the dvd's, so that i cant play them anymore.

I wonder what command i can use in order to get a raw dump of the data written to the dvd and somehow get the video out.

Hope someone can help.

Btw im running ubuntu 8.04 64 bit workstation.

Thanks.

---

### Post by aeiah on 2008-06-03
try
```

cat /dev/cdrom0 > name.iso

```
where cdrom0 is the name of your drive and name.iso is what you want to call your iso. it may not work but its the easiest thing to try first

---

### Post by aeiah on 2008-06-03
[or try this](http://www.acetoneiso.netsons.org/)

---

### Post by calraith on 2008-06-03
dvdisaster might also prove useful.

---

