---
title: "Can't get ATI AIW 9700 to capture video"
date: 2009-03-23
forum: Multimedia Software
---

### Post by drsk on 2009-03-23
I installed an ATI AIW 9700 Pro card on my 8.10 i386 box.  I went through the comprehensive video how-to on this forum and downloaded gobs of drivers, tool, etc., without error (no /dev/video0 file created, though.  Strange...). However, card seems to work fine (my monitor hasn't complained).  But how do I capture video from my camcorder, VCR, etc?  Ffmpeg needs a /dev file as input but there isn't one.  I ended up creating a /dev/video0 with mknod, but Ffmpeg says "no such file or directory."  The file exists, so what's up?

---

