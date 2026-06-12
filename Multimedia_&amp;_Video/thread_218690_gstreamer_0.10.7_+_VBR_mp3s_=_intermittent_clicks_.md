---
title: "gstreamer 0.10.7 + VBR mp3s = intermittent clicks &amp; pops"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by Oblong_Cheese on 2006-07-18
Hi all,

Just wondering if anyone can help me out with an annoying problem I have had ever since I installed Dapper about a month ago. While all sound playback works fine and dandy on my SoundBlaster Live 5.1 DE + ALSA + gstreamer 0.10.7 combination (with Rhythmbox, Quod Libet, Mplayer, Totem, etc), all players seem to suffer the same intermittent clicking and popping problem.

All of my mp3s are either VBR or CBR @ 320kbps, they're all excellent quality (ripped to the [Uberstandard](http://www.ubernet.org/?p=UberStandard)), yet some (not all) of my mp3s when played through the above software under Linux experience this clicking and popping.

In WindowsXP through the standard Creative drivers and foobar2000, there are no such strange audio issues. However, the music will intermittently click and pop when played through Quod Libet etc under Linux.

I am wondering if anyone else experiences this problem and if there is a way to fix it?

Thanks in advance.

---

### Post by Oblong_Cheese on 2006-07-20
Bump.

---

### Post by Oblong_Cheese on 2006-07-26
> **Oblong_Cheese said:**
> Bump.

Bumpity. :(

---

### Post by Oblong_Cheese on 2006-08-01
> **Oblong_Cheese said:**
> Bumpity. :(

More bumps.

---

### Post by talbain on 2006-12-18
i used to have many clicks and pops and distortion and saturation in linux with my soundblaster live 24bit the solutions was to set "system -> preferences ->sound" to use ALSA and the same for every single app i used audio on, then set the system volume to no more than 85% (its an ALSA issue with some soundblasters) and it works perfectly now.

Hope it helps, good luck.

---

