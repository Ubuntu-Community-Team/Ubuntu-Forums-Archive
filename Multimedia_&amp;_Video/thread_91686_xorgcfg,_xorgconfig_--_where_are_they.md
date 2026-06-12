---
title: "xorgcfg, xorgconfig -- where are they?"
date: 2005-11-17
forum: Multimedia &amp; Video
---

### Post by dsandber on 2005-11-17
Which packages contains the xorgcfg and xorgconfig tools?  And how would I figure this out for myself ( I tried ).

I know you can run Xorg -configure, but I thought these tools might be handy as well.

Thanks,

-Dan

---

### Post by Molikk on 2005-11-18
[QUOTE=dsandber]Which packages contains the xorgcfg and xorgconfig tools?  And how would I figure this out for myself ( I tried ).

I know you can run Xorg -configure, but I thought these tools might be handy as well.

Thanks,

-Dan[/QUOTE]

hmmm you mean xorg.conf??
```
/etc/X11/xorg.conf
```
and it's in with xserver-xorg but this package only make this file not contains it!

---

### Post by ubuntu_demon on 2005-11-18
to reconfigure your xorg :

$ sudo dpkg-reconfigure xserver-xorg

(I always choose default suggestions + the correct video driver + simple monitor configuration unless I get into trouble)

---

