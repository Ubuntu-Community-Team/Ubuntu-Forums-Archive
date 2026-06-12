---
title: "Sound trouble, microphone"
date: 2010-12-18
forum: Multimedia Software
---

### Post by ewpaisley on 2010-12-18
Hi everybody,

I recently tried out a solution [http://ubuntuforums.org/showthread.php?p=10241292#post10241292](http://ubuntuforums.org/showthread.php?p=10241292#post10241292) ) to my previous sound problem (not being able to record audio, after the initial problem of not being able to detect my internal microphones).

What I did was add a line with the text

options snd-hda-intel model=fujitsu-pi2515

To my alsa-base.conf file. This solved half the problem -- I can now get sound from Microphone 2, (albeit buzzy and low quality sound), but it can't detect any of my analog plug-ins. The computer doesn't respond to my headphones - by respond I mean "turn of the internal loudspeakers", and it also doesn't respond to the external, analog microphone I connected.

So I purged alsa, reinstalled, and I'm back to square one. I have a semi-fix for absolutely essential Skype-calls, but the quality is really low and the solution above seriously messes up the rest of my audio control.

I'm running a Fujitsu-Siemens Pa3515, and Ubuntu 10.10. Typing > sudo aplay -l gives me:

> card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

