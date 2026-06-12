---
title: "avi &gt; /dev/video0"
date: 2008-07-16
forum: Multimedia Software
---

### Post by dronchik on 2008-07-16
Hi, I have searched for a solution on making fake webcam in linux, like manycam or splitcam in windows, and have found AVLD another video loopback device. So i have compiled a module and loaded it. AMSN webcam configuration says that there is a v4l dummy video device, and i have /dev/video0. I tryied to play video on it with mencoder using mencoder video.avi -nosound -ovc raw -vf format=bgr24 -of rawvideo -o /dev/video0 and have success. But I really need to do that in graphic way, using mplayer, vlc or some other video player. Anybody can help me with that?
Or maybe there another solution for that? I cant beleave that there is no way in linux to do fake webcam.

Thank you and sorry for my bad english.

---

### Post by abhi2610 on 2011-06-09
Hey,

Did you find a solution for the same?

---

