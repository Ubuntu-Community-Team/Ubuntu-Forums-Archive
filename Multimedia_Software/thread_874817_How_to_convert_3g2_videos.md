---
title: "How to convert 3g2 videos?"
date: 2008-07-30
forum: Multimedia Software
---

### Post by ginnie6 on 2008-07-30
I'd like to add a movie to the sd card for my phone but need to convert it to 3g2 first. Does anyone know what program I could use to do that?

Thanks!!

---

### Post by FakeOutdoorsman on 2008-07-30
You can try ffmpeg:
```
ffmpeg -i input.avi -s 352x288 -ar 8000 -ac 1 output.3g2
```
The "-s" option is frame size.  You can choose other sizes with 3g2: 128x96, 176x144, 352x288, 704x576, and 1408x1152.  It will encode to a defualt bitrate of 200 kb/s.  If you want it higher then use the "-b" option like "-b 512k".

If you want a GUI for ffmpeg, then [WinFF]("http://winff.org") is a good program.

---

