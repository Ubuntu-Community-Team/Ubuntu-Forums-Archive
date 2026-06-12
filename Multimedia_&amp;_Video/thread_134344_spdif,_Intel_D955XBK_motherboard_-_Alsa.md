---
title: "spdif, Intel D955XBK motherboard - Alsa"
date: 2006-02-21
forum: Multimedia &amp; Video
---

### Post by skskarda on 2006-02-21
I have 2 channel analog audio working fine but cannot get the coax or optical to work.  

The details:
Ubuntu Breezy
Vanilla Kernal 2.6.15
Latest Alsa drivers, lib, and utils 1.0.11rc3
Intel D955XBK motherboard with on-board 7.1 with optical/coax digitial out
SigmaTel STAC9221

Alsamixer only shows PCM, Front, and Mic (no IEC 958 as described in howto's)

$ cat /proc/asound/devices
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I suspect it is a driver problem but I have the latest alsa driver and alsamixer is reporting:
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: SigmaTel STAC9221D A2 
This makes me believe that the driver is correct.   Am I missing something simple?

I get the same thing regardless of what I try:
mplayer file.wav -ao alsa:device=hw=0,0
mplayer file.wav -ao alsa:device=hw=0,1
mplayer file.wav -ao alsa:device=hw=0,2

It plays the sound on the analog port but not digital.

---

### Post by LiquidIQ on 2006-02-22
Try getting Alsa from CVS, I don't know if rc3 has all the changes. Let me know if that works.

---

### Post by skskarda on 2006-02-22
[QUOTE=LiquidIQ]Try getting Alsa from CVS, I don't know if rc3 has all the changes. Let me know if that works.[/QUOTE]

Thank you!!   CVS version fixed this.  Fantastic!

I made mistake of posting here before realizing the alsa users was the best place to post.  I will post the solution there also.

---

