---
title: "ProjectM-pulseaudio"
date: 2009-05-05
forum: Multimedia Software
---

### Post by sublimehypocrisy on 2009-05-05
Just followed the installation guide and I'm getting a segmentation fault. It seems that dozens of other people are having the issue, but I am yet to find a thread that repairs the problem.

--------------------------------------------------------------------------------------------------------------------------------
paco@paco-desktop:~/projectm/projectM-Trunk/src$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
[projectM] config file: /home/paco/.projectM/config.inp
No Textures Loaded from /usr/share/projectM/textures
set pipeline broken FIX ME
[projectM] Allocating idle preset...
[PresetFactory] path is Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[PresetFactory] url is idle://Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[projectM] warning: no valid files found in preset directory ""
call factory clear here?
call factory clear here?
unconnected: connecting... 
connectHelper:  "alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.monitor" 
Segmentation fault
--------------------------------------------------------------------------------------------------------------------------------

Any Idea's? Thanks for whatever help I get.

---

### Post by sublimehypocrisy on 2009-05-05
So I'm responding to this so it won't get ignored. It's a common crash and no one so far has fixed it. Can anyone suggest how I might compile more information about this error?

---

### Post by isaidi on 2009-08-31
anyone solve this yet ?
apparently it is a bug ...

[https://bugs.launchpad.net/ubuntu/+source/libvisual-projectm/+bug/193968/comments/7](https://bugs.launchpad.net/ubuntu/+source/libvisual-projectm/+bug/193968/comments/7)

```
The error was because a call to glGetintegerv asking for 
GL_MAX_TEXTURE_SIZE was returning 0 which caused a floating point exception 
when trying to calculate the texture width. I added a check to the source 
code inside SOIL.c to see if it was 0 and if it was forced it to 4096 which 
worked (which seems to be a common max texture size), although I am not 
sure of the proper solution to this.
```

---

