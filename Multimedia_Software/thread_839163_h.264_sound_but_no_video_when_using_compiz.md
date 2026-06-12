---
title: "h.264 sound but no video when using compiz"
date: 2008-06-24
forum: Multimedia Software
---

### Post by Poleh on 2008-06-24
Hi folks

finally got h.264 playback working with mplayer and ffmpeg and a LOT of reading. It plays fine when I am using the regular desktop, without compiz, but as soon as I enable compiz, I get sound but no video.

I don't even know where to begin to look at to find out, coz I am a n00b so am asking for some hints as to where I can do some more reading :D

Thanks in advance!

---

### Post by aeiah on 2008-06-24
launch mplayer (or gmplayer) from the command line with the x264 video and check for errors. hopefully its gonna spit back an error saying you need to change the video output with the -vo flag. you can set this in the conf file or in gmplayer, the configuration panel. i cant remember which ones are likely to work but you'll have a choice of several and one will work.

---

