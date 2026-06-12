---
title: "Sound is only faintly audible"
date: 2009-03-15
forum: Multimedia Software
---

### Post by poussecte on 2009-03-15
Hello all,

I just received a pre-installed ubuntu computer. I'm a new ubuntu user. The soundcard seems to be working but the sound which comes out is faintly audible. Any hints on how to get it to output with decent volume?

The sound card seems to be installed as shown by aplay -l command
**** Liste des PLAYBACK périphériques ****
carte  0: V8235 [VIA 8235], périphérique 0 : VIA 8235 [VIA 8235]
  Sous-périphériques: 4/4
  Sous-périphérique: #0: subdevice #0
  Sous-périphérique: #1: subdevice #1
  Sous-périphérique: #2: subdevice #2
  Sous-périphérique: #3: subdevice #3
carte  0: V8235 [VIA 8235], périphérique 1 : VIA 8235 [VIA 8235]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
jeanpaul@jeanpaul-desktop:~$ 

Any help appreciated,

best regards,

poussecte

---

### Post by poussecte on 2009-03-15
Forgot to mention I'm using rythmbox to read sound files.

The ryhmbox volume control is at maximum

I've also tweaked Alsa mixer to show all volume controls, and tested them indiviually, for all available devices. The volume controls which have an effect on sound ouptut are

- PCM
- "Volume general"

With all of these pushed at maximum the sound is only faintly audible. I'va also checked that none of them are on mute.

I checked using a portable mp3 player that the amplifier to which I have connected the computer is not the source of the problem

Cheers,

poussecte

---

### Post by poussecte on 2009-03-15
Problem solved, my bad, connexions inside computer had been disconnected during transport...

---

