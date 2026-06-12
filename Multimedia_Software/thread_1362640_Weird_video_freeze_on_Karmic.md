---
title: "Weird video freeze on Karmic"
date: 2009-12-23
forum: Multimedia Software
---

### Post by linuxgr on 2009-12-23
Hey all,
before I submit a bug I wanted to try and make sure I understand what's happening as well as see if anyone else has the same problem. It happened after upgrading to 9.10.

It is very weird; while watching a video, if I move forward or backward in time (with arrows or with mouse click on location), the video moves, plays for about 2 seconds and then freezes like it's paused. While it's frozen, every time I move in time, it again plays 2 seconds and goes back to freezing. The solution is to close video and open again.

I thought it had to do with Smplayer at first, but then I noticed it also happens on VLC and some other video players, and sometimes it also happens with audio files! Audacious for example seems to have a very similar behavior, but it is not caused every single time like with a video.

Can anyone else verify this?

---

### Post by rvm4000 on 2009-12-23
In smplayer try to select another audio driver (pulse or oss), in preferences -> general -> audio.

---

