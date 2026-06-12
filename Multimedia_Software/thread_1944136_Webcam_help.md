---
title: "Webcam help"
date: 2012-03-20
forum: Multimedia Software
---

### Post by spizzak on 2012-03-20
I'm using guvcview to turn off the auto-exposure on a webcam right now but I would like to do it from the terminal (without guvcview gui). From what I understand this should be done using uvcdynctrl but I can't seem to get it installed on Ubuntu 10.04

Any suggestions?

---

### Post by spizzak on 2012-03-20
Fixed- Just had to use  -DUVCVIDEO_INCLUDE_PATH= ... to specify location of uvcvideo.h

---

