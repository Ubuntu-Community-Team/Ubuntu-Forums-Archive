---
title: "Webcam works with xawtv, nothing else"
date: 2009-03-24
forum: Multimedia Software
---

### Post by lateralus01 on 2009-03-24
I've spent the last few hours trying to configure my webcam and I kinda pulled it off....sorta.  My cam is so messed up I can't even tell you what kind it is because there are many terms that refer to it:

MotionEye
05ca:1837
R5U870FLx86

I don't even know which one it is, all I know is that it uses the driver r5u870 but that driver doesn't work for kernel versions 2.6.28 (my kernel).  So there's this other project that makes it work by injecting ucode into the camera which allows it to work with the uvcvideo driver.  IDK I've spent forever screwing with it and now the camera does output video!  But the problem is, only one application allows it to work, xawtv.
Camorama, mplayer, neither can use my camera.

This brings me back to a page I had found earlier in my search:
[http://ogolberg.googlepages.com/fz140.html](http://ogolberg.googlepages.com/fz140.html)

This page is about configuring all of my hardware for gentoo.  There's a particularly important quote:

"This is a v4l driver and thus various v4l-compatible programs such as XawTV and Ekiga work with the camera."

Well actually Ekiga won't work either, it comes close because the little light above my camera will come on, but no video.

Anyway I want this webcam to work....on the internet....as a webcam.  As far as I've seen xawtv will just let me look at myself....useless unless I need a mirror.  It'd be great if it'd work with pidgin or something.

Any Ideas?

Thanks,
Lateralus01

---

### Post by lateralus01 on 2009-03-24
anyone?

---

