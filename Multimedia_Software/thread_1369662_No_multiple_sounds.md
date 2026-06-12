---
title: "No multiple sounds?"
date: 2010-01-01
forum: Multimedia Software
---

### Post by h2z on 2010-01-01
It seems that some apps do something when launched that causes sounds not to play (even though I can see the volume bar moving) when other applications are using the sound card :confused:

I first figured the applications switches from pulseaudio to ALSA but all of the volume meters in alsamixer are at their max.


The game "Assaultcube" for example - if I have rythembox playing and I start the game: there are no sounds (game or rythembox). And the only way to "restart" the sounds is to either restart rythembox or disable and re-enable the hardware profile.
If nothing is using the sound card, game launches with sounds. Same thing happens with wine (with all of the sound options available). Rythembox sounds work fine when other sounds are present (browser, movie player). I'm pretty sure it's something to do with the configurations (haven't changed anything).

The speakers/headphone are connected to the onboard (ATI SB analog) jacks.


Aplay returns:
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci:
```

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]

```

---

### Post by h2z on 2010-01-02
Bump, anyone?

---

### Post by h2z on 2010-01-06
This is getting very frustrating :(

---

### Post by Yellow Pasque on 2010-01-06
assaultcube uses SDL for audio. Have you tried installing using libsdl1.2debian-pulse?

---

