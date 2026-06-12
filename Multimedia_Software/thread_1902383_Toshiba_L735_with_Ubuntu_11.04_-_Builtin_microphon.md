---
title: "Toshiba L735 with Ubuntu 11.04 - Builtin microphone doesn't work"
date: 2011-12-30
forum: Multimedia Software
---

### Post by IlTavo on 2011-12-30
Hi, I have a Toshiba L735 and the builtin microphone does not work. Could someone help me to get this working please? 
I think that the ubuntu sound configuration is ok, the selected device profile is "Analog Stereo Duplex", in the Input Tab the Input Volume is 100% and not muted and the device sound input is in "Internal Audio Analog Stereo". However, when I talk the "Input Level" bars do not move.
I tried some workarounds like:
[http://ubuntuforums.org/showthread.php?p=9810690#post9810690](http://ubuntuforums.org/showthread.php?p=9810690#post9810690)
but it didn't work.

The alsa information is 
[http://www.alsa-project.org/db/?f=62b1e4ffc845de8a618ae64a2453b0721da969d4](http://www.alsa-project.org/db/?f=62b1e4ffc845de8a618ae64a2453b0721da969d4)

---

### Post by lidex on 2011-12-31
You have 4 mic channel elements:
```
Simple mixer control 'Mic B',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic C',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic E',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic F',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: [COLOR="Red"]Capture [on][/COLOR]
```
They're all mono, BTW.
Next you have the capture element - stereo, mind you - with both channels at the same level.
```
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
```
For simplicity's sake, drop the level of the left channel capture down to zero. Then try enabling your other mic channels, one-at-a-time. Use sound recorder to test.

---

