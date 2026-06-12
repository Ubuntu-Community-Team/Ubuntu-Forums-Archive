---
title: "Issue with sound and totem"
date: 2008-05-15
forum: Multimedia Software
---

### Post by entplex on 2008-05-15
I installed 8.04 fresh on my system a couple of days ago.  Well I was playing a .avi file with totem and paused, suspended the computer and woke it back up.  I noticed that mixer_applet2 was frozen and overloading one core on my cpu, so i killed the process (I'm fairly sure totem was still open while i did this). now totem has no sound, I have tried uninstalling it and reinstalling it with no luck.  All setting seem okay, so I'm not sure where to look.  I'm using an external Creative Extigy card and sound work through other applications.  One other thing on a side note that I noticed is that there is weird artifacting of playback when I rescale a window or do other basic things, I'm wondering if this might have to do with my sound card being USB? If anyone has things I could try or more info on getting the Extigy working optimally, please let me know.

---

### Post by michelepolo on 2008-10-14
> **entplex said:**
>  I'm using an external Creative Extigy card and sound work through other applications.  One other thing on a side note that I noticed is that there is weird artifacting of playback when I rescale a window or do other basic things, I'm wondering if this might have to do with my sound card being USB? If anyone has things I could try or more info on getting the Extigy working optimally, please let me know.

Hi. i'm too on an external extigy and as far as i know there are just two solutions for managing it: 1 cochran's oss drivers [http://exaudio.sourceforge.net/](http://exaudio.sourceforge.net/) and 2 alsa/ubuntu.

my advice is that if you stick to the extigy and use just that, disable alsa and use oss (either cochran's or "normal" oss)
otherwise look thru alsa website there are some configurations you may use

---

