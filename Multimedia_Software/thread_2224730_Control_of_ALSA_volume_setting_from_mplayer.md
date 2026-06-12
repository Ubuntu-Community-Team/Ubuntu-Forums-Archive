---
title: "Control of ALSA volume setting from mplayer"
date: 2014-05-17
forum: Multimedia Software
---

### Post by colin-bourassa on 2014-05-17
Prior to 14.04, I was able to adjust the "PCM" ALSA device volume with the volume control in mplayer. In Ubuntu 14.04, mplayer can still change its output volume, but it doesn't seem to be mapped directly to any of the ALSA volume settings.

How can I restore the previous behavior and have mplayer control the ALSA PCM volume? I'm set up to use ALSA directly (i.e. no Pulse).

--Colin

---

### Post by ronb19495 on 2014-05-17
try alsamixer just type alsamixer in a terminal

---

### Post by colin-bourassa on 2014-05-17
> **ronb19495 said:**
> try alsamixer just type alsamixer in a terminal

I have no problem changing ALSA device volume settings with alsamixer and other tools, but I'm trying to determine how to change the PCM (or Master) volume with the volume control in mplayer.

---

### Post by ronb19495 on 2014-05-18
I just installed mplayer-gui to see what you are talking about but it appears mplayer-gui doesnt want to work on 14.04. smplayer works fine

---

### Post by ronb19495 on 2014-05-18
I just installed gnome-mplayer it works fine but no pcm control in mplayer, I put the volume up on the task bar and it nearly blew my head off, but I have all my alsamixer volume setting up to 82

---

