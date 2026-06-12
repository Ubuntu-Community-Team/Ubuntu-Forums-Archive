---
title: "compaq presario c500 problems"
date: 2008-07-26
forum: Multimedia Software
---

### Post by mindstalk on 2008-07-26
This laptop had had standard "main speakers don't mute when head phones plugged in" problems, which I'd solved in the usual way, I think 
options snd-hda-intel model=laptop
in /etc/modprobe.d/alsa-base

I upgraded to Heron today (and wasn't that a bundle of joy; I *think* the locales problem is straightened out, but for a while zsh was segfaulting) and the headphones worked, but all sound was horribly distorted.  I solved that per recommendations by turning the sound down and then up in mplayer -- perhaps the top task bar control would have worked as well.  Then it was too quiet, but I fixed that somehow, maybe using alsamixer, I forget.

But now there's one last problem: the buttons on the laptop don't work.  Above the keyboard there's the wireless button, the power button, volume down, volume up, and mute.  The latter three still make volume-related images appear on the screen but they have no effect on the actual sound, while they definitely did so before the 'upgrade'.  This is poor.  Help, please?

---

### Post by mindstalk on 2008-07-27
Bump for attention.

---

