---
title: "seekable wmv (Windows Media) stream"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by Lary Grant on 2007-01-03
Is there any player that will allow me to "seek" (move backward or forward in time) while viewing a Windows Media (wmv) stream?

---

### Post by pay on 2007-01-04
Try mplayer```
sudo aptitude install mplayer w32codecs
```Make sure that you have the repositories needed opened (universe?). Then you can use the arrow keys to seek.

---

### Post by Lary Grant on 2007-01-05
When playing a .wmv  stream with mplayer, all the "seek" keys (arrow, etc.) either crash mplayer or don't work.

---

### Post by pay on 2007-01-05
Try mplayer rc1, seeing as it natively supports the vc1 codec, it might be more stable.

---

