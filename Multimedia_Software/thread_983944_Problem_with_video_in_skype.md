---
title: "Problem with video in skype"
date: 2008-11-16
forum: Multimedia Software
---

### Post by Angelo Furno on 2008-11-16
Hi.
Video from webcam in skype blinks! I had the same problem with any video player but I solve it by changing the video output module to X11. How can I do the same with skype (2.0). I have not fount such an option for the video output.

ASUS F7se, webcam Chicony Electronics Co., Ltd 1.3 MPixel UVC Webcam, Ubuntu hardy heron 8.04.1, kernel 2.6.24

Thank you!

---

### Post by anlazarov on 2009-03-01
Yeah, I've got the same problem :S Anybody?

---

### Post by krlhc8 on 2009-03-05
I start skype in a terminal with this command to get video working for me: 

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

