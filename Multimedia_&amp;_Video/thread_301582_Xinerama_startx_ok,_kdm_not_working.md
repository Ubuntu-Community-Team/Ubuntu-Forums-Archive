---
title: "Xinerama: startx ok, kdm not working"
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by incunabulum on 2006-11-17
Hi there,

on my Dell Inspiron 510m laptop I currently have problems getting kdm to work correctly with xinerama.

What works is:
/etc/init.d/kdm stop
startx -> Ok

I am pretty shure this means I do have a valid and working xorg.conf configuration file. 

What does not work is:
/etc/init.d/kdm start (or reboot)
> only internal screen works

Does anyone know what might be the reason for this strange behaviour??? xorg.conf is unchanged, no changes whatsoever are done. Shouldn't kdm read xorg.conf or execute startx somehow?

Any ideas are welcome,

thx, Michael

kubuntu edgy eft

---

