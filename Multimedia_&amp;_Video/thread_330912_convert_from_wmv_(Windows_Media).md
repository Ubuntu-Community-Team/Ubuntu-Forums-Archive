---
title: "convert from wmv (Windows Media)"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by Lary Grant on 2007-01-03
Is there any way to convert from a .wmv (Windows Media) file to anything else (i.e. mpeg) that can be burned onto a standard DVD?

---

### Post by pay on 2007-01-04
Yeah. Use mencoder.```
sudo aptitude install mplayer
mencoder in.wmv -ovc lavc -oac lavc -o out.mpg
```And read this [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html)

---

### Post by Lary Grant on 2007-01-05
Thanks for the command... I tried it but the output has lots of dropped frames and no sound.

---

