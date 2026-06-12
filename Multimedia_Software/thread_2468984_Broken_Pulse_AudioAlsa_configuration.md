---
title: "Broken Pulse Audio/Alsa configuration"
date: 2021-11-16
forum: Multimedia Software
---

### Post by cliffwilliams44 on 2021-11-16
Yeah, I broke it, my fault!

I'd left my earbuds home one day last week and figured I'd run over to Walmart and grab a new pair for $5. Got back to my office and connected them to Bluetooth and the microphone did not work.

Googled it and there were several solutions. Tried one that most people said would work, one part was installing pipewire, this did not work at all. So I undid this as the instruction said. When I got home my original earbuds did not work.
Tried re-installing PulseAudio/ALSA and that failed big time.

One of the instructions is to run: sudo alsa force-reload
All this does is output: unloading audio drivers and lists the drivers and then hangs. I let it hang there most of the day. This also causes the system to become sluggish and unresponsive.

Is there a way to put this all back the way it was when Ubuntu 20.04 was installed?

My only other option is to reload the OS. Not a huge deal but it is a time waste. I need my audio as we've abandoned phones in our office. (all MS Teams)

---

### Post by slickymaster on 2021-11-16
Thread moved to **Multimedia Software** for abetter fit

---

