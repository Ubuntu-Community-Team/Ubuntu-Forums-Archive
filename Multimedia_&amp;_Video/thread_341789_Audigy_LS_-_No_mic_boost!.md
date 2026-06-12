---
title: "Audigy LS - No mic boost!"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by Zaggy on 2007-01-19
Sound works, but microphone volume is very low, and I can't find the Mic Boost checkbox.

Output of amixer controls:

> numid=16,iface=MIXER,name='Mic/Line in Capture'
numid=15,iface=MIXER,name='Capture Source'
numid=3,iface=MIXER,name='Analog Center/LFE Playback Volume'
numid=1,iface=MIXER,name='Analog Front Playback Volume'
numid=2,iface=MIXER,name='Analog Rear Playback Volume'
numid=4,iface=MIXER,name='Analog Side Playback Volume'
numid=9,iface=MIXER,name='CAPTURE feedback Playback Volume'
numid=7,iface=MIXER,name='SPDIF Center/LFE Playback Volume'
numid=5,iface=MIXER,name='SPDIF Front Playback Volume'
numid=14,iface=MIXER,name='SPDIF Out'
numid=6,iface=MIXER,name='SPDIF Rear Playback Volume'
numid=8,iface=MIXER,name='SPDIF Unknown Playback Volume'
numid=17,iface=PCM,name='IEC958 Playback Default'
numid=18,iface=PCM,name='IEC958 Playback Default',index=1
numid=19,iface=PCM,name='IEC958 Playback Default',index=2
numid=20,iface=PCM,name='IEC958 Playback Default',index=3
numid=10,iface=PCM,name='IEC958 Playback Mask'
numid=11,iface=PCM,name='IEC958 Playback Mask',index=1
numid=12,iface=PCM,name='IEC958 Playback Mask',index=2
numid=13,iface=PCM,name='IEC958 Playback Mask',index=3

Is this a bug?
Even my onboard el crappo sound had a mic boost feature :( 
( I did disable onboard sound)

---

### Post by josesanders on 2007-01-23
Have you seen this:
[http://ubuntuforums.org/showthread.php?t=343216](http://ubuntuforums.org/showthread.php?t=343216)

---

### Post by Zaggy on 2007-01-23
Thanks for the response, but I run Dapper.
I tried compiling a newer alsa-driver, that got me sound with Alsa, I haven't had luck with OSS yet though.

---

### Post by Krieg on 2007-11-28
So, this thing was never fixed I guess, because I have the same problem.

---

