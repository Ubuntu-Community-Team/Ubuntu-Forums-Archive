---
title: "ALSA 5.1 volume control problem"
date: 2011-09-04
forum: Multimedia Software
---

### Post by BreatheInMyVoid on 2011-09-04
Hello. I have VIA C-Media 5.1( CMI8738 ) with my 5.1. 
My 5.1 do not have hardware volume controller and I have some problems with volume control using system mixer. It does not work correctly 
when I use surround51 and when I use ALSA for playing stereo on surround 
sound setup. If I do not setup enything and use just my two speakers it
works well.

My .asoundrc for stereo on surround:

pcm.!default {
type route
slave.pcm surround51
slave.channels 6

ttable.0.0 0.5
ttable.1.1 0.5

ttable.0.2 0.5
ttable.1.3 0.5 

ttable.0.4 0.25
ttable.1.4 0.25

ttable.0.5 0.25
ttable.1.5 0.25
}

When this setup enabled my mixer works incorrect, music is too loud
and i can control it only in player(using Benshee). And if I watch 
movie using surround51 system mixer controls only two speakers 
How I can set up it correctly?

---

