---
title: "redirect v4l2 webcam stream?"
date: 2010-10-16
forum: Multimedia Software
---

### Post by sergiom99 on 2010-10-16
Hi there,
in my company's intranet we have a flash-based video-chat app (sort of chatroulette) that only takes input from a video camera.
My laptop webcam is mapped at /dev/video0 and the flash app sees it as 'HP Webcam V4L2'.
I want to direct a video (in Kaffeine or Mplayer) clip or an Oo presentation to this app. (Now I point the camera back and forth to another PC)

Is there a way to redirect the stream and make it pose as a webcam to be detected by other apps as a webcam? Maybe /dev/video1.

I tried with
```
mplayer video.avi > /dev/video1
``` but didnt work.

Hope I made myself clear.
Thanks for your help.

---

### Post by sergiom99 on 2010-10-17
Here's the answer I think:
[http://sourceforge.net/projects/webcamstudio/](http://sourceforge.net/projects/webcamstudio/)

---

