---
title: "removing pulseaudio"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by shoofy on 2007-08-29
Today I decided to purge my system of pulseaudio, since it's caused me nothing but headaches since installing it a while ago (unless it came preinstalled and I just messed with it...). In any case I had followed the pulseaudio "perfect setup" guide, which is not so perfect, and now I've tried to undo all those changes, but some applications that worked with pulseaudio now don't work.

For example, totem and xine both open and then hang immediately. VLC crashes as soon as anything starts playing, Totem and VLC both throw this error before crashing:> ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave

What do I have to do to bring my sound back that doesn't involve reinstalling pulseaudio?

---

### Post by shoofy on 2007-08-29
never mind, reinstalling the alsa packages and rebooting solved it. I'm not sure whether reinstalling alsa was necessary or not.

---

