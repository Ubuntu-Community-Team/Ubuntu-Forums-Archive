---
title: "no sound from nForce2 card on gOS"
date: 2009-08-06
forum: Multimedia Software
---

### Post by paean on 2009-08-06
Hi folks,
I recently installed gOS 3.1 (based on ubuntu). 

[B][I]$uname -a
Linux m 2.6.24-24-generic #1 SMP Fri Jul 24 22:46:06 UTC 2009 i686 GNU/Linux[/I][/B]

The sound card is detecting.
[I]
[B]$ lspci | grep audio
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)[/B][/I]

The sound choices selectable in the sound prefs are
nforce2, 
nforce2 iec958, 
ALSA, 
OSS.
Autodetect

It appears ALSA picks it up fine as well.

[B][I]$aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/I][/B]

So, all that to say... I don't get any sound from the speakers!

I've checked and unchecked a variety of mute buttons using alsamixer, alsamixergui, gnomealsamixer and the default volume control app that comes with gOS. 

My speakers work fine on my FBSD box, so I know the speakers are okay. 

Any thoughts?

Thank you kindly,
Adam

---

