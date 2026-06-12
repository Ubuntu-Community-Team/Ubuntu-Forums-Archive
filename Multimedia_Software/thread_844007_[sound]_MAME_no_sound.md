---
title: "[sound] MAME no sound"
date: 2008-06-29
forum: Multimedia Software
---

### Post by kakyoism on 2008-06-29
I got xmame + gxmame working perfectly except that there is no sound.
I switched the sound device from /dev/dsp to .../dev/dsp0 ~ /dev/dsp2, then to /dev/audio, still no sound.

Help!

---

### Post by carlob on 2010-01-23
I don't know about xmame, but I had and audio problem with sdlmame and I solved it by going to synaptic and installing the package libsdl1.2debian-pulseaudio (this automaticllay removes libsdl1.2debian-alsa).
After this, sdlmame automatically recognizes my audio driver and everything goes ok.
See also [this thread]("http://ubuntuforums.org/showthread.php?t=1370466").

---

