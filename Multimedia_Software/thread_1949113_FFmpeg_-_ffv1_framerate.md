---
title: "FFmpeg - ffv1 framerate??"
date: 2012-03-29
forum: Multimedia Software
---

### Post by Halbblutplins on 2012-03-29
In the future I want to record my desktop for some tutorials etc. and therefoe I want to use FFmpeg. The problem is that I want to use the lossless codec "ffv1" because it is really fast on my system and that I can't control the framerate. In my script I set the fps on 30 but it shows me that it is recording only 10 -12fps.

My script: ```
ffmpeg -f alsa -ac 2 -ab 44800 -i pulse -s 1366x768 -f x11grab -i :0.0 -r 30 -qscale 1 -acodec mp2 -vcodec ffv1 /....../screencast.avi 
```I hope someone of you is able to help me!

---

