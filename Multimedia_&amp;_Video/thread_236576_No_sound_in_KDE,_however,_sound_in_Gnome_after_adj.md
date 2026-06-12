---
title: "No sound in KDE, however, sound in Gnome after adjusting OSS PCM2 everytime. 6.06LTR"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by Robertjm on 2006-08-15
Hi all,

I've been fighting a problem with my sound levels for a bit now. Thought I had it licked, but the settings don't seem to want to stay.

When I'm in Gnome I don't have any sound when I'm running the Alsa device (in default mixer, not Alsa-gui). I adjust the PCM setting to full, but don't get any sound whatsoever. If I change the device to the OSS device I see that PCM2 is set to zero sound. When changing that the sound starts just fine. I can then change to the Alsa device again and its still working. What's odd is that now if I adjust the PCM level (not PCM2) inside the Alsa device the sound is now!!

if I restart the computer the PCM2 setting persists. HOWEVER, if I go into KDE there is a quick blast of sound (akin to a warning sound, I guess), and then there is no sound, no matter what I adjust. There is no PCM2 in KMIX and PCM is set to zero. However, when I try adjusting the PCM level it doesn't do me any good (just like in Gnome w/Alsa device).

Now, when I reboot into Gnome there is zero sound, and I have to adjust the PCM2 level in the OSS device again.

I followed the HOWTO sticky in this forum, but the setting doesn't seem to stick, even though I did the "save settings" part down the article.

I have a Creative Labs Soundblaster Live w/Live Drive. The emu10k1 driver is loaded and in my modprobe list and after making my changes did "sudo alsactl store 0" per the instructions in the HOWTO.

Anyone else having the same problems? If so, did you fix it, especially getting sound working in KDE? That's my prefered desktop environment if I can get the sound working.

Thanks!!

Robert

EDITED: Changed notes once I realized sound does persist in Gnome once levels are changed, as long as you don't try using KDE.

---

### Post by Robertjm on 2006-08-15
OK, so I discovered the Volume Control setting within KDE so I can now duplicate the workaround of using the OSS device to set PCM-2 level, and then switch to the ALSA device after that.

What's maddening is that while the volume persists in Gnome after restarting the computer, it goes silent again after restarting and going into KDE.

Is there some type of command/script I need to run at ther terminal to have KDE remember the volume settings??

Robert

---

