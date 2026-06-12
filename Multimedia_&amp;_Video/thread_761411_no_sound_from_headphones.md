---
title: "no sound from headphones"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by egyong06 on 2008-04-21
hello everyone! i'm new to unbuntu (7.10). from my Toshiba Satellite A135-S4666 i have sound from its onboard speaker but no sound from headphones port. both, HDA Intel (alsa mixer) & Realtek ALC861-VD (OSS Mixer) no sound at the headphone port. please help!!! & thanks in advance...

---

### Post by kpkeerthi on 2008-04-21
Open a terminal window and type **alsamixer**. Make sure the mixer channel for headphone is not muted or has low volume level.

> Use left/right arrow keys to navigate.
> Press 'm' to toggle mute/unmute. MM means muted. OO means unmuted.
> Use up/down arrow keys to raise volume.
> Press 'Esc' to quit alsamixer.

---

### Post by egyong06 on 2008-04-21
thanks for the reply! opened alsamixer, chosen HDA Intel (alsa mixer) which has the headphone volume control-cranked all the way up-STILL NO SOUND from it. (the Realtek ALC861-VD (OSS Mixer) doesnt have volume control for headphones). what else could be done? i wonder

---

