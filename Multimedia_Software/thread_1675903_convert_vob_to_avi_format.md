---
title: "convert vob to avi format"
date: 2011-01-26
forum: Multimedia Software
---

### Post by yaron86 on 2011-01-26
how can i convert vob format to avi?
is there a simple and nice program?

i am using ubuntu 10.04
thanks a lot

---

### Post by ajgreeny on 2011-01-26
Probably winff which uses ffmpeg as its backend.
Try ```
ffmpeg -i file.vob file.avi
```in terminal as well, though you can set the output quality as you want with lots of options.
Winff is probably easiest.

---

