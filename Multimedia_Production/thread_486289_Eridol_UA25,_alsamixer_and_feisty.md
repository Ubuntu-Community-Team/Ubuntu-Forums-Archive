---
title: "Eridol UA25, alsamixer and feisty"
date: 2007-06-27
forum: Multimedia Production
---

### Post by fredj on 2007-06-27
When I plug my UA25 in, Audacity can see it, Jack can see it and System-Preferences-Sound can see it.
I can use aplay to play back wav files to it. The only thing that can't see it is alsamixer. So when I try to 
start Jack it won't start because alsa says it can't access the hardware.

Anybody know what the answer to this is?

---

### Post by fredj on 2007-06-28
When I read the Jackd error messages more carefully, it was obvious that the alsa backend was
complaining about my trying to use 32 frames with this device. When I increased that to 64 the problem
disappeared.

---

