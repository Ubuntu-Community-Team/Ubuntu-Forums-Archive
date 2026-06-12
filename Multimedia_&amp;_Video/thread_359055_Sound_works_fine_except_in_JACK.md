---
title: "Sound works fine except in JACK"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by d_b on 2007-02-11
Hello,

I have a HP nc8430 C2Duo laptop with Intel ICH7 audio.  The sound works fine with straight ALSA -- I can play music, watch movies, run QSynth, etc.

However, if I try to get audio running through JACK, it gets heavily distorted and crackled.  I tried many different configuration options for JACK to no avail (Force 16bit, 44100KHz vs 48000KHz, realtime, etc).  

Has anyone experienced a similar problem? 

Thanks,
d.

---

### Post by d_b on 2007-02-20
As per suggested in this post, increasing the number of buffers to 4 did the trick(although I still get more XRUNs that I would like to!)

[http://www.ubuntuforums.org/showthread.php?t=313819&highlight=jack+ardour](http://www.ubuntuforums.org/showthread.php?t=313819&highlight=jack+ardour)

---

