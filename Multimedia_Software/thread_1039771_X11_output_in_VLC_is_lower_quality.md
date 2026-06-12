---
title: "X11 output in VLC is lower quality"
date: 2009-01-14
forum: Multimedia Software
---

### Post by joey_breizh on 2009-01-14
I've been having problems with videos flickering on VLC when running VLC and Compiz simultaneously. I looked around and found that the problem could be solved by switching the video output from Default to X11 in VLC ([here]("http://ubuntuforums.org/showthread.php?t=707770") and [here]("http://ubuntuforums.org/showthread.php?t=974321") for example).

That does work for me, however there's a BIG loss in video quality when I switch to the X11 output. Does anyone have an idea why or how I could maintain the video quality with the X11 output?

(I have an ATI Radeon Xpress 1100 and the proprietary drivers installed.)

---

### Post by CarpKing on 2009-01-15
X11 is lower-quality by nature.  It probably shouldn't be noticeable at the video's native size, but fullscreen (or even double-sized) it will be pixelated.  Xv (the one that has trouble with Compiz on the proprietary drivers) was created and is default for a reason.  If you don't play any 3d games, you might want to investigate how well your card is supported with the open-source drivers.  They aren't as fast, but video works fine with Compiz.  You may be in luck, though: there are rumors that ATI will fix the problem on their drivers soon.

---

### Post by joey_breizh on 2009-01-15
Ok, thanks for your reply! 

I don't play any 3D games but sounds like it might be worth just waiting for ATI to get their act together on this one. I've found that with SMPlayer the quality is more than decent even full screen, which is why I was hoping there was something that could be tweaked on VLC, since I've always used VLC as my default player. But I guess I'll go over to SMPlayer for a while!

---

### Post by binbash on 2009-01-15
If you have a big loss in quality, you should consider disabling compiz while playing videos (dont forget to change the output)

---

