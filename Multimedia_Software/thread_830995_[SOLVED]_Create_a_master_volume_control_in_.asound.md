---
title: "[SOLVED] Create a master volume control in .asoundrc"
date: 2008-06-16
forum: Multimedia Software
---

### Post by cogadh on 2008-06-16
So I've decided to revisit an old problem of mine, the lack of a master volume control in ALSA with my Audigy LS. I have already used a custom .asoundrc to make all of my 5.1 speakers work, but I have to control the volume through three separate controls (Analog Front, Analog Rear and Analog Center/LFE). I would like to be able to have a single volume control that adjusts the volume as a whole, while retaining the ability to fine tune the volume with the individual controls I already have. Here's the current contents of my .asoundrc:
```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}
```
What do I need to add to create a working master volume control?

EDIT - Also, since upgrading to Kubuntu 8.04 (finally successfully did it this weekend), I've noticed that the volume I set on the Analog Rear and Center/LFE controls using the Kmix applet does not "stick" with a reboot. If I use alsamixer to set the volume and then do "sudo alsactl store", it also doesn't retain the volume settings for those channels. Any ideas on that one?

EDIT2 - Okay, I fixed the problem with the volume setting not "sticking". Apparently, if you use the Kmix applet instead of Kmix from the Multimedia menu, it won't retain the settings. Once I switched to using the menu one, everything was fine. Still need help with creating the master volume control though.

EDIT3 - Well, looks like I found my own "workaround"  for this issue. I swapped out my speakers for a different 5.1 set that has its own master volume control on the center channel speaker. Since I no longer have to worry about the individual channels losing their volume settings in ALSA, this solution will do.

---

