---
title: "1366x768 working for X, VLC playback not right..."
date: 2009-03-14
forum: Multimedia Software
---

### Post by geekfound on 2009-03-14
Hey guys,

Have got a Dell Studio 1555, running 8.10 (AMD64)...  Nearly everything was detected when I installed, except for the video card HD 4570, which I installed by downloading Catalyst 9.2...  After a reboot it was working at native resolution of 1366x768, everything looks as it should, except:

Trying to play a DVD (Season 1 Frasier) using VLC, and it's totally skewed.  Have played with Aspect Ration / Crop / Zoom and haven't been able to get it to look right.  When I go full screen, half the time it comes up completely black and the other half of the time it mirrors the windowed version and looks askew...

I tried fooling with the Video -> Monitor Pixel Aspect Ratio setting in VLC (4:3,16:9) and didn't have any luck.

Any ideas?

Cheers

---

### Post by markbuntu on 2009-03-14
In Tools/Preferences/Video try setting the output to X11 video output and put everything else back the way it was. Some people have reported that OpenGL also works for them with the fglrx driver. 

You can also try checking the accelerated video output box.

---

### Post by geekfound on 2009-03-14
Yup, had just been playing with those- X11 works and OpenGL flickers.

Thanks very much, solved!

---

