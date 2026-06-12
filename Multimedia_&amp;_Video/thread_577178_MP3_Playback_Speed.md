---
title: "MP3 Playback Speed"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by catnippants on 2007-10-15
Folks,
  I've come across a strange problem I can't seem to fix.    For some reason, all my MP3s seem to play back a little slow - I'd say about 10-20%, and the pitch is lowered accordingly.   I've tried banshee, rhythmbox, Exaile, and even XMMS.    My MP3s are all ripped from CDs at 192K constant bitrate.   I have two soundcards in my system, with the default being an M-Audio Audiophile 2496 (ice1712 ALSA driver) set via a file in /etc/modprobe.d.

At one point I was able to get things to work properly by loading an MP3 into Audacity and playing it.   It played at the right speed, and then after that all the other apps played at the right speed too.   I haven't been able to reproduce this because Audacity seems to continually drop my M-Audio card - it ends up not being listed in the Playback Device dropdown.

I'm wondering if this is tied up in either the ALSA 48K vs 44.1K issue, or if the players are defaulting to playing my 192K files at 128K.    It just seems like there's some default setting somewhere I'm missing.   Any thoughts or ideas?   I've read everything I can find on setting up sound and I just can't figure this out....

Thanks,
Mike

---

### Post by violinchris@gmail.com on 2007-11-17
I just posted a similar problem.  I did search but didn't find yours until after.  I will watch this thread if someone replies to you, but maybe you should watch mine as well.   	
**"frequency too too with M-Audio Audiophile 2496"** I have a 2496 as well, so I am assuming we have the same problem.  Chris

---

