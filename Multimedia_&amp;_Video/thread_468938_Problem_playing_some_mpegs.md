---
title: "Problem playing some mpegs"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by tpg on 2007-06-09
I'm having the occasional problem with some mpeg files ... in that they don't play! I'm running kubuntu, and have tried kaffeine, xine and mplayer, and this particular file won't play. Here's a link: [http://media.ereslibre.es/2007/06/klistviewselections.mpeg]("http://media.ereslibre.es/2007/06/klistviewselections.mpeg") that doesn't work for me. However, other mpegs do work!?! Does anybody have any ideas, and thanks in advance!

---

### Post by reclusivemonkey on 2007-06-09
Plays fine for me. I use the mplayer firefox plugins.

---

### Post by tpg on 2007-06-10
OK, I fixed it. It seems to be specific to integrated graphics chips, using the xv driver and high resolution videos. The fix is to add
```
Option "VideoRam" "65536"
Option "CacheLines" "1980"
```
No idea why it works, but it does!

---

