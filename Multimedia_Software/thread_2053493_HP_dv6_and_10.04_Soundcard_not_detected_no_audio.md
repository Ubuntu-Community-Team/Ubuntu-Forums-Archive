---
title: "HP dv6 and 10.04: Soundcard not detected no audio"
date: 2012-09-05
forum: Multimedia Software
---

### Post by landersohn on 2012-09-05
I recently got an HP dv6-7014nr. I am running Ubuntu 10.04 64 bit.
Problem is I can not get sound to work. 
After a clean install of 10.04 I copied the installation from my older laptop over. everything went fine except for sound.

I removed pulseaudio and tried a few things. What it seems to come down to is this:

aplay -l returns device_list:223: no soundcards found
alsa-info alse shows no sounds cards, the /proc/asound directory does not exist and alsamixer fails with "no such file or directory"

lspci shows an Intel Audio device (1e20) BUT running 

lspci -v for sound chard shows under
[Capabilities]: (access_denied)

---

### Post by landersohn on 2012-09-05
Solved, at least to some extend.
After running the AlsaUpgrade script the sound card was recognized and I get some audio (even though not through the Beats Audio system).

---

### Post by gordintoronto on 2012-09-05
In my experience, the best solution to sound card problems is to run the current version of Ubuntu. There are constant kernel fixes in this area.

---

