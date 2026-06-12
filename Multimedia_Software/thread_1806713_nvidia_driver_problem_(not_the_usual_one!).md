---
title: "nvidia driver problem (not the usual one!)"
date: 2011-07-18
forum: Multimedia Software
---

### Post by therecklessengineer on 2011-07-18
Hi chaps,

Bit of a newbie here - been using Ubuntu for a few months now and loving it! I've had the usual nvidia driver problem - but I've manually installed the latest drivers from the nvidia site.

But, I've got an issue, and no amount of Googling seems to return an answer.

When playing an HD file playback is not GPU accelerated. If I play it in VLC with "Enable GPU Acceleration (experimental)" checked, then it plays just fine. However, if I try and play in anything else (including video editing software) then the playback is very jumpy.

(If I play it in Windows, it works perfectly too).

I've checked what drivers the playback software is using - I've tried everything on the list. Only X11 and OpenGL result in it working at all - but it remains jumpy/jerky.

It seems to me that for some reason, the CPU is doing the heavy lifting rather than the GPU. Playback is accompanied by the cacophony of the CPU fan ramping up to full jet speed.

So how can I shift the work to the GPU where it is supposed to be?

---

