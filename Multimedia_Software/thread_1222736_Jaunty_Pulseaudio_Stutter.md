---
title: "Jaunty Pulseaudio Stutter"
date: 2009-07-25
forum: Multimedia Software
---

### Post by kakyoism on 2009-07-25
On HP dv-3, Looks like I've got sound, with the mod-probe.d/alsa.conf one line fix, "options snd-hda-intel model=?"

my model should be "dell-m4-1", 

but the sound stuttering a lot of people reported is happening to me too.

I tried tuning the recommended lines in daemon.pa, default.pa, asoundrc...
None of them worked. 

Is it an ALSA bug?

Someone recommended that an experimental kernel fix solved this problem. I really wonder if it's safe to install an experimental kernel...


Any other ideas???

Thanks!

---

### Post by martinbaselier on 2009-07-25
It's not really helpful to start several threads about the same problem at the same time. I just happened to read some of the others (I don't know how many you started). But centralizing the information in one thread is helpful to understand the problem for people trying to help. 

Besides it's bad policy. The worst thing that could happen when installing a new kernel is your system not starting. The next worst thing is getting error messages.

---

