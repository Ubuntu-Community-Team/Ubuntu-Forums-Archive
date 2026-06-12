---
title: "LogitechQuickCamPro9000"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by Tevion on 2008-02-16
Hi, 

I just get an LogitechQuickCamPro9000 and tryed to make it work.
On [http://blog.gnist.org/article.php?story=Linux_and_LogitechQuickCamPro9000](http://blog.gnist.org/article.php?story=Linux_and_LogitechQuickCamPro9000) I found a good step by step instruction but at the testing I got a problem:

........ -desktop: luvcview -L
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
ERROR opening V4L interface 
: No such file or directory

Cane enyone help me with this ERROR please?

Thank you
Tevion

---

### Post by jakommo on 2008-02-17
Hi,

the error is "No such file or directory"
are you in the "video" group?
what do you get with ls -la /dev/video* and lsusb ?
did you try as root?

---

