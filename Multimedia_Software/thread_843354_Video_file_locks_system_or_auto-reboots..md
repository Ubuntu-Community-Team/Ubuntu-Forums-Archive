---
title: "Video file locks system or auto-reboots."
date: 2008-06-28
forum: Multimedia Software
---

### Post by Beto on 2008-06-28
Lately my Hardy installation locks up or reboots when trying to play a video. It is independent from the player, as it happens in VLC, Totem, Xine, etc...

Jun 28 09:21:29 beto-laptop kernel: [ 4232.281346] bonobo-activati[12931]: segfault at aaaaaaaa eip b7e5a852 esp b5efca50 error 4
Jun 28 09:21:45 beto-laptop pulseaudio[13095]: pid.c: Stale PID file, overwriting.
Jun 28 09:21:45 beto-laptop pulseaudio[13095]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 28 09:21:45 beto-laptop pulseaudio[13095]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 28 09:21:45 beto-laptop pulseaudio[13095]: alsa-util.c: Cannot find fallback mixer control "Mic".

These were the messages at the time of the problem.
Any ideas how to solve it?

---

