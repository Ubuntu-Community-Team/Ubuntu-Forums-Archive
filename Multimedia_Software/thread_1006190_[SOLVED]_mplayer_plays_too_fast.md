---
title: "[SOLVED] mplayer plays too fast"
date: 2008-12-09
forum: Multimedia Software
---

### Post by morty35 on 2008-12-09
I am trying to get a youtube video to play on my background.  When I use mplayer to run the .flv file, it plays way too fast.  I used ffmpeg to convert it to a mpg, but now the quality of the video is considerably less.  

How can I get the video to play at the right speed and be high quality.

---

### Post by morty35 on 2008-12-09
I figure it out.  the quality is the same.  It takes a moment for the images to go switch to higher quality.  When it plays fast, it is harder to notice the low-quality to high-quality transition.  I was able to fix it using the -fps command.  The file properties said 24 fps.  For some reason, mplayer was playing it at 50 fps.  

mplayer -fps 24 video.flv

that did the trick.

---

