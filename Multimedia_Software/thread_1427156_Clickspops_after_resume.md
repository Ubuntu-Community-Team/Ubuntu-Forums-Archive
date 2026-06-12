---
title: "Clicks/pops after resume"
date: 2010-03-11
forum: Multimedia Software
---

### Post by Lorso on 2010-03-11
Hello,

This is a problem I've noticed since my first installation of UNR 9.10 on my HP mini 311c 1010SL 2 months ago. This netbook uses MCP79 HDA Nvidia controller.

Flawless audio when system starts, but if I suspend and then resume audio output is full of clicks and pops, not too loud but quite annoying (like reproducing from a dirty vinyl ;)). I must shutdown and restart (it seems that a simple reboot isn't enough) to restore a clean audio.

Currently running kernel 2.6.31-20 (but problem went through 31-14 and 31-19).
I've tried to upgrade pulseaudio to 1.0.21  and alsa to 1.0.22 via repository (ricotz/unstable and ubuntu-audio-dev), but nothing apparently changed.
From Synaptic I see Alsa packets at 1.0.22, but if I run a
```

cat /proc/asound/version

```
I see it's still 1.0.20

Thanks a lot,

L.

---

