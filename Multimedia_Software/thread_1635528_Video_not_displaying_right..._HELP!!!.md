---
title: "Video not displaying right... HELP!!!"
date: 2010-12-01
forum: Multimedia Software
---

### Post by kitsune7 on 2010-12-01
Whenever I try to display a video in any movie player (except on youtube.com for some reason) the video player shows it only for a split second and then the video display goes black.  The audio still plays, no error comes up, and the video displays in short bursts if you consistently move the window around.  What's up with that?

I found /etc/X11/xorg.conf doesn't exist though /etc/X11 does.
What do I do?

---

### Post by lovinglinux on 2010-12-02
Are you talking about a standalone movie player or videos embedded in web pages? Are you talking about flash or other types of video?

---

### Post by kitsune7 on 2010-12-02
Videos embedded in web pages run fine (flash specifically), but all standalone video players I've tried can't run any video type without this problem.

---

### Post by lovinglinux on 2010-12-03
Follow the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") and will be able to play almost everything.

Personally, I use smplayer, which is great.

---

### Post by kitsune7 on 2010-12-04
I tried installing smplayer and tested it with a few videos.  Surprisingly they all played perfectly.  Why would that be?  Is there any connection between the video problem and the fact that I can't enable any desktop effects?

---

### Post by lovinglinux on 2010-12-04
> **kitsune7 said:**
> I tried installing smplayer and tested it with a few videos.  Surprisingly they all played perfectly.  Why would that be?

I'm not sure, but I guess smplayer could be using a different video output ([see xv]("http://en.wikipedia.org/wiki/X_video_extension")).

> **kitsune7 said:**
> Is there any connection between the video problem and the fact that I can't enable any desktop effects?

Possibly. You might be experiencing issues with the default video driver in regard to video overlay.

---

### Post by kitsune7 on 2010-12-04
Hey thanks :D
That helped a lot.

I think I'll stick with video players that support the X video extension and do a little more research concerning compiz and my graphics card.

---

