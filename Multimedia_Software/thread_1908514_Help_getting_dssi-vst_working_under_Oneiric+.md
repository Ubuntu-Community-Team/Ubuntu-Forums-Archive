---
title: "Help getting dssi-vst working under Oneiric+"
date: 2012-01-13
forum: Multimedia Software
---

### Post by immerohnegott on 2012-01-13
Currently, dssi-vst lists wine1.3 as a dependency both in Oneiric and Precise, which sort of breaks things since that branch doesn't have (or at least isn't compiled with) support for JACK. This forces the use of ALSA/Pulse and the JACK module for Pulse, which at least in my case is completely non-functional. VSTHOST segfaults whenever a plugin tries to load (the error message goes something to the tune of not being able to find an audio device). I submitted a bug about the dependency/packaging mishap, but it remains unassigned.

I attempted to use the KxStudio repo, which worked for a little while, until an update borked the whole thing. I haven't tried compiling from source yet (which honestly, might be the best route).

Anybody know of another repo that houses a working version of dssi-vst? I'd like to be able to upgrade my studio machine to Precise when it drops, but it looks like I'm stuck with Natty/Mint 11 until this gets fixed.

---

### Post by lykwydchykyn on 2012-01-13
What's the URL for the bug you filed?  I'll be happy to confirm it, because I'm having the same issue.

Unfortunately I don't have an answer....

---

### Post by immerohnegott on 2012-01-13
[https://bugs.launchpad.net/ubuntu/+source/dssi-vst/+bug/898218](https://bugs.launchpad.net/ubuntu/+source/dssi-vst/+bug/898218)

---

