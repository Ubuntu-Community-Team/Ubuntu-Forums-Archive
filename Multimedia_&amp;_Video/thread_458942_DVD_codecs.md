---
title: "DVD codecs"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by pepitosir on 2007-05-30
i m new in Ubuntu. I follow the instructions from documentary to install codecs for DVD player, but is not working. It is so complex to wach a dvd? 
I try to edit the /etc/apt/sources.list but I dont have permisions. I set my self to belong in almost all groups, but I dont have permisions to save the file. any help about?

---

### Post by renzokuken on 2007-05-30
you need to use sudo to edit that file

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by eye208 on 2007-05-30
You can manage software repositories by opening System -> Administration -> Software Sources. You will be asked for your password. There's no need to edit system files by hand at this point.

Probably the easiest way to watch DVDs is to use VLC media player (from the "universe" repository). You can install it from the applications menu ("Add/Remove ..."). VLC supports a lot of media formats out of the box, e.g. MPEG-2 (DVD), MPEG-4 (DivX, Xvid, H.264), MP3, AAC, WMV/WMA ...

---

