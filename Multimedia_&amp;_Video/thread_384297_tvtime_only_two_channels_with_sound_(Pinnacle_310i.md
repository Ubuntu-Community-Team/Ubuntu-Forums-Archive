---
title: "tvtime only two channels with sound (Pinnacle 310i)"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by MR Bacardi on 2007-03-14
Hello

I'm trying to set up tvtime with my tvcard Pinnacle 310i.
I have all the channels with video, but I am only getting sound on two of the channels (the first two - lowest frequezys)
I've tried searching the net for solutions, but I can't seem to find anyone which works.

I have written the following to my /etc/modprobe.d/options file:
options saa7134 card=77 tuner=54 gbuffers=32 vbibufs=32 audio_ddep=10 tsbufs=32 alsa=1 latency=64

But I must admit I don't know what any of it means (except from card=77 and alsa=1)

---

### Post by MR Bacardi on 2007-03-15
The problem is not only within tvtime, but also in XawTV
Still hoping for someone to help me out?

---

### Post by MR Bacardi on 2007-03-15
Got it working :)
I just edited the options file again, and made it back to
options saa7134 card=77 tuner=54 
To anyone with similar problems:
Try my solution, but remember to turn on the input device in alsa mixer.

---

