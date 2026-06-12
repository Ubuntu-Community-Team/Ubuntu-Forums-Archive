---
title: "Watching widescreen movies on my widescreen tv via s-video"
date: 2008-06-09
forum: Multimedia Software
---

### Post by jbrown96 on 2008-06-09
I got an unused P4 system and have installed Mythbuntu 7.10 on it. While I haven't done anything Myth-related, I watch movies from my laptop, using NFS. Everything works great, except the display. Most of the movies (.avi) are widescreen (16:9), which is also the aspect of my TV, but they always show up with the black bars on top and bottom. I think that the problem is the S-video link but I'm not sure. 
I have set the display type as widescreen in the Myth control center. I use VLC to watch movies. 
What I would like to know:
Is there some setting that I'm missing? Is there a video player that could stretch the picture somehow (doesn't have to be VLC)? Is there a program that could convert the video (I have tried DeVeDe and Avidemux), or a ffmpeg command to do it?

Thanks for the help

---

### Post by attari on 2008-06-09
> **jbrown96 said:**
> I got an unused P4 system and have installed Mythbuntu 7.10 on it. While I haven't done anything Myth-related, I watch movies from my laptop, using NFS. Everything works great, except the display. Most of the movies (.avi) are widescreen (16:9), which is also the aspect of my TV, but they always show up with the black bars on top and bottom. I think that the problem is the S-video link but I'm not sure. 
I have set the display type as widescreen in the Myth control center. I use VLC to watch movies. 
What I would like to know:
Is there some setting that I'm missing? Is there a video player that could stretch the picture somehow (doesn't have to be VLC)? Is there a program that could convert the video (I have tried DeVeDe and Avidemux), or a ffmpeg command to do it?

Thanks for the help


Did you try the following option in VLC menu?

Video > Aspect-ratio > 16:9

:KS

---

### Post by pk386 on 2008-06-09
I'm wondering the same thing but I want to setup Freevo to fill my screen...

[http://ubuntuforums.org/showthread.php?t=819989]("http://ubuntuforums.org/showthread.php?t=819989")

(Subscribed to thread)

---

### Post by jbrown96 on 2008-06-10
> **attari said:**
> Did you try the following option in VLC menu?

Video > Aspect-ratio > 16:9

:KS

I could've sworn that I've tried this before, but it worked. 16:9 made the black bars a little better, but 4:3 fixed everything.

In VLC-->Video-->Aspect Ratio-->4:3

---

### Post by macstyle@freeshells.ch on 2008-06-19
I've made it..

Force freevo with overscan option and force in the config file the aspect ratio in the file.I've put aspect ratio of 16:9 because i've black bars on left and right :D

---

