---
title: "Opening any video file crashes the video player (totem, VLC)"
date: 2008-05-21
forum: Multimedia Software
---

### Post by swingline on 2008-05-21
I tried to play a .avi file by double clicking it (opens totem), the codecs weren't there so I agreed to install them all (just quickly checked all the boxes). Apparently that was stupid, because now anytime I try to open a video, the application crashes. I then downloaded VLC to remedy this problem, but the EXACT thing happens; the application crashes.

My screenlets were glitched until I restared them all. Even after rebooting...however that could be unrelated.

I'm running a dual monitor setup with my laptop. But the laptop LCD is just off. I have an nVIDIA GeForce 6200, which was difficult to configure.

---

### Post by swingline on 2008-05-22
Does anyone have a similar problem? or any problems opening video files which cause their video player to crash?

---

### Post by Xiong Chiamiov on 2008-05-22
VLC uses internal codecs, so it's a great way to separate out codec problems from something else.

The only thing I can think of is (aside from bad files) that Compiz is doing something odd, since I know it does something with videos.  I'm not sure quite what, since it's a recent addition to my desktop, but you might try turning that part of it off (sorry, no idea how to do that in GNOME).

---

### Post by f37u5g0d on 2008-12-04
I had the same problem and I turned compiz completely off and then turned it back on (extra) and now I can watch videos again.  I think that it is one of the plug-ins but IDK which one.  I don't think it is the video playback plugin because I turned that one off and on before restarting compiz and it did not help.

---

### Post by f37u5g0d on 2008-12-05
I was wrong.  It wasn't compiz that was the problem for me it was RhythmBox being open!  I think it was something to do with sound because I was fooling around with those packages the other day.  Anyway for me as long as rhythmbox is not open than my totem (or VLC) works fine.

---

### Post by arrancaru on 2008-12-05
I had this problem until changed my video card drivers. The opensource drivers of my ati radeon doesn't support video and desktop effects at same time, apparently. Try disable desktop effects and see if video playback is back. If you have a nvidia or intel you're luck, i guess. You can install proprietary drivers and get desktop effects without video flickering.

---

