---
title: "sound continues after quiting tvtime"
date: 2010-11-02
forum: Multimedia Software
---

### Post by chinmay3 on 2010-11-02
Hi everybody.
I have winfast tv200 expert tv-tuner.
I am using TvTime to watch tv through it. Everything is working fine except that sound continues to come even after i quit tvtime. is there any solution for it?
 Thank's in advance.:(

---

### Post by xc3RnbFO8P on 2010-11-02
**Alt - F2**

**Stop**
> pulseaudio -k 
**Start**
> pulseaudio -D

---

### Post by leedemo on 2010-11-02
hey i have this same problem, i see this post here,

[http://ubuntuforums.org/showthread.php?t=281829](http://ubuntuforums.org/showthread.php?t=281829)

but i cannot get this to work for me. let me know if it works for you?

-Lee

---

### Post by fresnofred on 2010-11-10
try synaptic and download gnome alsa mixer and see if muting any of the boxes will kill the sound.  i had to attach cd cable from card to motherboard, after opening the pc, and have to unmute for tv sound and mute to turn it off (cd slider box) but it worked for me.  have to use gnome alsa mixer each time i watch tv with tvtuner, but minor inconvenience.

---

