---
title: "Pulseaudio 5.1 Issues"
date: 2011-09-21
forum: Multimedia Software
---

### Post by xur17 on 2011-09-21
When I use VLC player or SMPlayer I am unable to get 5.1 sound output (it only outputs to my front left and front right speakers (and leaves out the rest).  I do have these set to 5.1 sound though.

Also, if I try the following command, all of my speakers work correctly, and the sound it output to the proper speaker:

> speaker-test -Dplug:surround51 -c6 -l1 -twav

---

### Post by BicyclerBoy on 2011-09-21
With VLC change the audio preferences settings to use alsa surround51

or run from cmd line
vlc --aout alsa --alsa-audio-device surround51

something similar for (s)mplayer must exist.

Using alsa devices (like this) will stop your shared system wide sound from working but that's not really a bad thing.

---

### Post by xur17 on 2011-09-21
I ended up reinstalling ubuntu.  I was having some other small issues, and figure it was worth the effort.

---

