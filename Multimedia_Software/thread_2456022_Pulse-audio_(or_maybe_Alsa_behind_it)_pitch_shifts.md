---
title: "Pulse-audio (or maybe Alsa behind it) pitch shifts when opening apps or streams"
date: 2021-01-02
forum: Multimedia Software
---

### Post by chrysanthemum2 on 2021-01-02
Does anyone else experience this or know what causes this?
When I open audacity, or start a virtual machine, or sometimes when i watch a youtube video, the pitch of all audio changes, usually higher (people talking on youtube sound like they've had helium!) but sometimes lower. It then resets to normal pitch if I restart pulseaudio using 'killall pulseaudio'.

---

### Post by orangecat-seth on 2021-05-02
I have this exact issue, but only with audacity... Using Pop! OS 20.10.. I am also unsure about what's at fault, but it seems to be a sample rate mismatch.
In my case, pulse is seemingly outputting at a higher sample rate than alsa is sending to the sound card, sounds like 48k being played back at 44.1k, with some crackling from it skipping samples.

---

