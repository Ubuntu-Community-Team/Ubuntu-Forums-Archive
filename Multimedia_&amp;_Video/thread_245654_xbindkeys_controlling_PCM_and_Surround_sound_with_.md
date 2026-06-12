---
title: "xbindkeys controlling PCM and Surround sound with 1 key???"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by dragonlor20 on 2006-08-28
Does anyone know a way to make 1 key execute more than 1 command in xbindkeys? I want my keyboard volume controls to maintain my equalizer under alsamixer by moving everything in equal numbers (for example: move pcm -1 AND Wave_Surround -1)... Or if anyone knows of a better sound controller for surround sound, that would be even better, but I still want my keyboard volume controls to work... Right now my xbindkeys controls only 2 of my 5.1 speakers and that makes volume control from the keyboard a bit awkward... 

Thanks in advance,
Scott

---

### Post by jannol on 2006-10-09
doesn't & work?

I don't know what version of xbindkeys you have but this is how I do it in my xbindkeys

ex
(xbindkey '(F12) "gedit & gcalctool")

also I can bind even more on release if I like too like this
(xbindkey '(release F12) "mousepad")

---

