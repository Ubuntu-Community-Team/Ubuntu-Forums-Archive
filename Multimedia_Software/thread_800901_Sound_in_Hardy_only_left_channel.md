---
title: "Sound in Hardy only left channel"
date: 2008-05-20
forum: Multimedia Software
---

### Post by David Miller on 2008-05-20
Hi

For some reason the sound on my machine has started to play only out of the left channel. I have tried adjusting the alsamixer settings, but none of them seem to change anything. I'm not sure what I did to cause this - it was fine as of last week. my soundcard details when I type aplay -l are as follows:

> 
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any ideas anyone?

Many thanks

David Miller

---

### Post by Sukarn on 2009-04-19
I have started having exactly the same problem, with different hardware than the OP.

aplay -l shows
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Sound has played fine on this laptop since the OS was first installed at Intrepid release time, but has suddenly started playing on the left channel only (in built speakers as well as headphones) today.

I tried restarting and checking alsamixer as well as gnome volume manager. I also checked gstreamer-properties and Sound preferences. Nothing seems to help with this issue.

I've also found other threads on this issue with no solution to the problem.

---

