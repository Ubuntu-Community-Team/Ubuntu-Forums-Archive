---
title: "[SOLVED] Sound only in media player"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by bahdom on 2007-10-20
Hi :D
I upgraded from feisty to gutsy yesterday. Anyway, sound wasnt working [ i use usb headphones which have their own external sound card]. So i went to the sound control panel and configured everything to use alsa [which worked in feisty] and put the mixer in "USB Audio (Alsa Mixer)", but still nothing had sound.
I tried using VLC player but it didnt have sound either. However, if i manually set the device in VLC to the headset in the ALSA tab it would work.

Help please :D

---

### Post by bahdom on 2007-10-21
this fixed it:

> **mohnkern said:**
> If you're using Alsa (which unless you changed it, and  you're using Feisty is likely) start by trying the following:


**[INDENT]asoundconf list[/INDENT]**


This will list the sound devices available to you, on my machine it looks like this:

Names of available sound cards:
Live
V8237
U0x46d0x8d7
Headset


Now type:

**[INDENT]asoundconf set-default-card <device>[/INDENT]**

Likely It will be:

**[INDENT]asoundconf set-default-card Headset[/INDENT]**

Some people have said they have to type the above command several times and reboot x (or sometimes their machine) to get it to work.

---

### Post by awells527 on 2007-10-31
That solved my USB audio problem.  Thanks for posting a solution.

---

