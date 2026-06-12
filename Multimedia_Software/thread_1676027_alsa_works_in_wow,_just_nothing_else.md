---
title: "alsa works in wow, just nothing else"
date: 2011-01-26
forum: Multimedia Software
---

### Post by drazgoth on 2011-01-26
H'lo

I uninstalled pulseaudio and wow runs GREAT, good frame rate, happy.. just sound is gone everywhere else now.  I went through the sticky guide, my computer recognizes the sound card, etc. I just don't know how to get sound working again for everything else but wow.  Any ideas? =/

---

### Post by roguebuck on 2011-01-26
i have a problem much like this, but smplayer is the only app i can get sound out of.

this didnt fix it for me; but i found that pulseaudio to default to mute when alsa was selected. by my deduction, this means that all applications except smplayer are outputting to pulse and smplayer is going to alsa?

maybe there is a confusion between the two audio servers.

---

