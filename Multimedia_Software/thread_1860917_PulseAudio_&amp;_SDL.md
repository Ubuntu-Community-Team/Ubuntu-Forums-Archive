---
title: "PulseAudio &amp; SDL"
date: 2011-10-15
forum: Multimedia Software
---

### Post by ilmalcom on 2011-10-15
It seems like PulseAudio has always had problems living with SDL. In my case, I have stuttering sound and glitches when I run ScummVM and ZSNes, which is annoying. I already tried the following solutions:

1. Changing the output driver in the applications

2. Setting SDL_AUDIODRIVER to esd

3. Disabling pulseaudio with pasuspend before launching the applications

No luck until now. I searched the web, but I was not able to find any working solution. Can anyone help?

---

### Post by Götz on 2012-02-23
I had also sound glitches, and I solved it (in 11.10) by installing libsdl1.2debian-pulseaudio. libsdl1.2debian-all should also work.

---

