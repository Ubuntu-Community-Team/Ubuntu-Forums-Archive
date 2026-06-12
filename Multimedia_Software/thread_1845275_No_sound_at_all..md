---
title: "No sound at all."
date: 2011-09-16
forum: Multimedia Software
---

### Post by Raziekiel on 2011-09-16
My sound stopped working yesterday and I can't figure out why. I've checked the basics, everything is plugged in, the sound works in windows.
It's not muted, and I checked with alsamixer as well. I checked, and I'm in the audio group, so it doesn't seem to be a permissions issue.

Running:
 sudo aplay -l
Gives:
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So it seems to be detecting my sound card.

Any ideas??

---

