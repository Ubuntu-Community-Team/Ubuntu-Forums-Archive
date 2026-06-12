---
title: "ALC883/MCP55 Surround Sound in wrong order"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by Moustacha on 2008-04-09
Hi, I've had a good search of the interwebs and have come up broke. I've got surround sound connected to my onboard audio, ALC883.
The plugs are in the right jacks (colour to colour) and this works on XP.
Not changing the plugs, ALSA wants to swap surround with centre/LFE. So centre becomes RL, LFE becomes RR and so on. It sometimes fixes itself in VLC, but everything else like Xine don't want to, they decide they'll use the bad way.
I found the alsa channel test, and it shows what I knew

```
speaker-test 1.0.14

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 5440
Period size range from 32 to 2720
Using max buffer size 5440
Periods = 4
was set period_size = 1088
was set buffer_size = 5440
 0 - Front Left
 4 - Centre
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE

```
I would assume the numbers are supposed to be in order, but no, it's decided to make it fubar. FL and FR are right, but the others....

Is there any way of sorting this out?

---

### Post by Metaljaz on 2008-04-11
Try this link..

[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)

---

### Post by eliazu on 2008-04-19
i have the same problem and i cant find how to fix it.
the link didnt help.
anybody have an idea?

---

### Post by Moustacha on 2008-04-19
My only solution is changing the plugs, which isn't very elegant =\

---

