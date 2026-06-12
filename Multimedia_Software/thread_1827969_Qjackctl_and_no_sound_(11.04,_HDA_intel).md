---
title: "Qjackctl and no sound (11.04, HDA intel)"
date: 2011-08-18
forum: Multimedia Software
---

### Post by kalpar on 2011-08-18
Qjackctl worked fine starting with Ubuntu 10.10, until I upgraded to 11.04.
Even after the upgrade, the audio works fine as long as I don't start qjackctl(and jackd).
After Qjackctl starts, all programs using audio (totem, banshee, Youtube) hang.
As soon as Qjackctl is terminated, these programs go back to their normal operations.
There are no messages in the Qjackctl message window that recognize these programs as clients.
so I tend to think this is a problem between jackd and these clients, rather than one between jackd and the audio hardware. 
But Qjackctl's own client seems to connect to the jackd server OK.
BTW, my audio setup is alsa and HDA intel, according to Qjackctl

Any help would be greatly appreciated

---

### Post by CatKiller on 2011-08-18
Those things won't output to JACK. For the kinds of thing that you want to use JACK for you won't want any of that running anyway. There's a plugin in the repositories that will take PulseAudio output (what those things are using) and feed it into JACK.

---

