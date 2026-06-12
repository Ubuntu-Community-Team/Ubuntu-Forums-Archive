---
title: "sound broken for just one user"
date: 2010-05-10
forum: Multimedia Software
---

### Post by bkline on 2010-05-10
After upgrading to lucid we found that sound is broken for my daughter's account, though it's working fine for my account and my wife's.  My daughter's account has three dashes for the sound indicator applet where my wife and I have the wave icon showing how high the volume is turned up, and the applet just shows a dummy output for the broken account where we have the real device:
.
```
bkline@fam:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any clues where to start looking?

---

### Post by bkline on 2010-05-14
Found it.  On the Hardware tab of the Sound Preferences applet I noticed that "Analog Stereo Input" was selected.  Don't know how that happened (very unlikely my daughter tampered with it, as she's very good about avoiding things she doesn't understand, but who knows), but setting it to "Analog Stereo Duplex" solved the problem.

---

