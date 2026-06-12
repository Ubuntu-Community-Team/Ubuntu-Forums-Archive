---
title: "Internal speakers problem"
date: 2008-09-10
forum: Multimedia Software
---

### Post by lesliek on 2008-09-10
I've installed v 8.04 on an IBM PC300. The specifications for the computer say "one pair of internal speakers". I can't get them to work, though I get sound via headphones.

I'm able to create a beep from the command line, but I don't know whether the sound comes from one or both of the internal speakers (or even from a third speaker devoted to system sounds).

I used the comprehensive sound problem solutions guide.

"aplay -l" gets:

**** List of PLAYBACK Hardware Devices ****
card 0: SI7018 [SiS SI7018], device 0: trident_dx_nx [Trident 4DWave]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  [obvious entries omitted]
  Subdevice #31: subdevice #31
card 0: SI7018 [SiS SI7018], device 1: trident_dx_nx IEC958 [Trident 4DWave IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The guide said I should therefore run alsamixer. I did and unmuted and turned up the volume of everything I could find. Still no sound.

What should I try next?

Thanks for reading this,

Leslie

---

### Post by Xavier Oddmon on 2008-09-27
The beep you hear is probably coming from your PC speaker, which is usually seperate from the speakers you would use to play music on. So, getting the beep to play is probably not your speakers working. Sorry. I have quite the opposite case, actually. I have no PC speaker, so i can't get beeps to work...

---

### Post by markbuntu on 2008-09-27
Try cat /proc/asound/modules and we will see if ALSA has found the right module for that card. It should be

module snd-trident

---

