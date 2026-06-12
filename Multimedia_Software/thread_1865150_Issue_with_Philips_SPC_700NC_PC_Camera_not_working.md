---
title: "Issue with Philips SPC 700NC PC Camera not working in skype."
date: 2011-10-19
forum: Multimedia Software
---

### Post by Sahasrahla on 2011-10-19
I've downloaded cheese and the cam works fine, It's just that I can't do it in skype. I remember long ago I was able to find some command in terminal that would fix this problem but for the life of me I can't seem to find that through google. 

lycid lynx
Philips SPC 700NC PC Camera
 skype version 2.2.0.35

---

### Post by no2498 on 2011-10-20
open a terminal type
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
click enter

---

### Post by Sahasrahla on 2011-10-20
Thank you, that was it.

---

