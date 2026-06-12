---
title: "Sequential thumbnail tools"
date: 2010-10-14
forum: Multimedia Software
---

### Post by Scifer on 2010-10-14
I was looking for a sequential thumbnail generator tool and found this one:
[http://moviethumbnail.sourceforge.net/](http://moviethumbnail.sourceforge.net/)

Does anybody know a better one or some that is in repository?

---

### Post by Scifer on 2010-10-14
Is it possible to generate sequential thumbnails like Movie Thumbnailer directly in mplayer?

---

### Post by Scifer on 2010-10-17
> **Scifer said:**
> Is it possible to generate sequential thumbnails like Movie Thumbnailer directly in mplayer?
```
mplayer -benchmark -nosound -quiet -zoom -vf scale=420:-3,tile=6:6 -vo jpeg:outdir=. -sstep 60 file.avi
```BUT. How to place the upper bar with video information like filename, duration, resolution, aspect ratio, audio and etc?

---

