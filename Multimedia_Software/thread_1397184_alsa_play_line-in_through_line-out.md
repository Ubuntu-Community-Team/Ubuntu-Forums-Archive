---
title: "alsa: play line-in through line-out"
date: 2010-02-03
forum: Multimedia Software
---

### Post by dabrowsa on 2010-02-03
kubuntu 9.10 without pulseaudio: 

How do I use alsa to play line-in through my speakers? 
I'm using 

arecord -f cd -D hw:0 | aplay -f cd 

but I doubt that's the best method; in particular the latency is awful.  Is there something more sophisticated?  A way to use the aloop module in my asoundrc?

---

