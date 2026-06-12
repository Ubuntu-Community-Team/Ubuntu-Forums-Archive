---
title: "No sound - just static fuzz"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by bathtoy on 2008-03-12
Setup:

- Ubuntu Studio 7.10
- Sound Blaster Audigy value

Sound worked perfectly after installing the system!
... now it has just turned into to a flat static fuzz, that sounds the same whether its a song or a system chime.

I have tried everything I can to fix it. I reinstalled selecting "LADSPA and DSSI" and the problem was immediate.

I found that deselecting DSSI and LADSPA solved the problem... that is until it stopped working again.

I run a "dpkg-reconfigure xserver-xorg" and installed some updates other than that I don't know what could have caused it. 

I have reinstalled 3 times, and I would GREATLY appreciate it if ANYONE could help me.


- TO SOLVE the problem I purged ALSA and OSS, and one LADSPA related item that had been installed in the repository. 

- I then reinstalled alsa and OSS, but not the LADSPA item

---

