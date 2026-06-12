---
title: "build-in webcam doesn't work"
date: 2009-08-28
forum: Multimedia Software
---

### Post by Ampi on 2009-08-28
I have an Acer Aspire One and it's impossible for me to get my webcam working.
For example Skype and Cheese don't see I have a webcam. So I installed luvcview 

apt-get install luvcview

and that seemed to install well.
But after

dmesg |grep -i "uvc"


I just get a new prompt. And when I want to test it:

luvcview -f yuv

I get the following error:

luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such file or directory


Any idea what I can do to get my webcam working?

---

### Post by Ampi on 2009-09-15
No ideas at all...?

---

### Post by Ampi on 2009-10-07
Sorry to bump, but really nobody has any idea how I can get the build-in webcam of my acer aspire one working?
Is is a common problem?

---

### Post by Ampi on 2009-10-31
Even after upgrading to 9.10 it doesn't work..

---

