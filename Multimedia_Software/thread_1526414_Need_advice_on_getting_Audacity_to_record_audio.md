---
title: "Need advice on getting Audacity to record audio"
date: 2010-07-08
forum: Multimedia Software
---

### Post by sofasurfer on 2010-07-08
I can play a music file with audacity but thats as far as I can get. I connected a cd player from its headphone output to my pc mic input and Audacity does not pickup the audio.

Any suggestions?

---

### Post by tgalati4 on 2010-07-08
Open a terminal:

alsamixer

Hit the tab key once until "Capture" is highlighted.  Use the up arrow to bring up the level.

In audacity, choose monitor to see the sound levels for the microphone.  If you don't see levels bouncing around, then perhaps your microphone is not set up correctly.  Post the output of:

aplay -l

arecord -l

---

### Post by lidex on 2010-07-09
Have a look here:
[http://forum.audacityteam.org/viewtopic.php?p=75044#p75044]("http://forum.audacityteam.org/viewtopic.php?p=75044#p75044")

---

