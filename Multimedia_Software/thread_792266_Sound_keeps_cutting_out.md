---
title: "Sound keeps cutting out"
date: 2008-05-12
forum: Multimedia Software
---

### Post by Pap3r on 2008-05-12
Hi all.  After the 8.04 update, my sound started doing weird things.  For instance, I'll play a game, then go back to listen to music, and none of my music players will play anything.  If I play music while playing a game, I receive no problems.  At times while playing games, I have the sound cut out on me and not turn back on.  I use alsa
```
pap3r|joe-desktop~| aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
It is listed, even when the sound won't turn on right now.  A restart of the xserver solves the problem every time.  Any ideas?

---

