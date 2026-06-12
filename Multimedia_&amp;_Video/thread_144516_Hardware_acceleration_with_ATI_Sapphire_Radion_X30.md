---
title: "Hardware acceleration with ATI Sapphire Radion X300SE"
date: 2006-03-14
forum: Multimedia &amp; Video
---

### Post by Ian Maxwell on 2006-03-14
I'm fairly new to really using linux (as opposed to playing around with it), and I'm learning a lot as I go along. I've gone through the guide [here]("http://ubuntuforums.org/showthread.php?p=408111") to try and configure my video card, but it seems the hardware acceleration still isn't working. I say this because

(1) Software that should run at pretty normal speed.... doesn't. (A dual processor P4 with that graphics card shouldn't have trouble running a GL screensaver.)

(2) 3ddesktop, when I try to start it up, gives an error:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
```

Any ideas?

---

### Post by Ian Maxwell on 2006-03-14
Nevermind, I figured out my problem--when I went through setup, I had chosen "ati" instead of "fglrx" for a driver.

---

