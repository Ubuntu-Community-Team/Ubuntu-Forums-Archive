---
title: "ALSA and my nvidia nforce MPC55 (Sigma Realtek STAC9277) Please help."
date: 2008-07-25
forum: Multimedia Software
---

### Post by msmr on 2008-07-25
First off, this is probably the 4th time I install ubuntu to start off new again mainly because I screwed stuff up, reinstalled, and started over again and learned.

This time I decided I was going to use my onboard sound instead of my X-FI

When I put aplay -l into terminal it gives me
```
msmr@TARDIS:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Now when I got into ALSA mixer, and go into the sound prefernces, everything is set up for the HDA nvidia device (my integrated device)

Everything is unmuted, my headset is plugged in the right ports, (no I didn't remove my X-FI card, when I have my integrated audio turned on it overrides the X-FI card iirc) 

It will not play, I've tried everything trying to see if something is muted, everything is set up right, the thing is, even in the LIVE CD i can't hear anything?

Can you tell me what I'm doing wrong?

Thanks.

---

