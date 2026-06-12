---
title: "Xonar Essence ST Not Working"
date: 2011-05-23
forum: Multimedia Software
---

### Post by kamper59 on 2011-05-23
Hello,

I'm running Ubuntu 11.04 x32, and after some research I haven't succeed getting my soundcard to work. 

Soundcard is detected but not sound comming from speakers.

This is what aplay -l says:

```

card 0: STH6 [Xonar ST+H6], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: STH6 [Xonar ST+H6], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Anybody can help me please?

---

### Post by aniruddha on 2011-08-07
Hello, I seem to be having the same issue as well. Same output for aplay -l as well. Has anyone gotten the Essence ST working on Lucid, alsa 1.0.21? Am really not sure I want to go through the whole alsa upgrade process.

---

### Post by aniruddha on 2011-08-09
no-one?

Update: So installing the alsa drivers from the ubuntu-audio-dev ppa seems to have fixed most issues. I would recommend that to all users having problems with this card.

---

### Post by Aliavaruus on 2011-08-23
There seems to be a driver issue with ALSA and the H6 expansion board

My Xonar Essence was working fine untili i got the H6 expansion board and now i have no sound with it connected.

Works fine in windows tho.

---

### Post by Aliavaruus on 2011-08-23
I followed the instructions in 

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

and now i have sound back again

---

