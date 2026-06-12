---
title: "Alsa output to multiples devices"
date: 2016-03-09
forum: Multimedia Software
---

### Post by xsnake_ on 2016-03-09
Hello,

I am trying to configure alsa to output sound to two devices at the same time. First off, here's the output of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Currently, my .asoundrc contains the following:
```
defaults.pcm.device 3
```

The above is required because flashplugin will only play sound on the default device, and my laptop is almost always connected to the TV (thus HDMI output). For the times I use the laptop when it is not connected to the TV, I would like to be able to have sound without modifying .asoundrc and restarting firefox. I am looking for a simple way to output to device 0 and 3 of card 0 with a proper .asoundrc configuration. Any ideas?

Thank you.

---

### Post by marseille2 on 2016-03-25
Take a look at some of these suggested solutions:


[LIST]
[*][http://www.6by9.net/output-to-multiple-audio-devices-with-alsa/](http://www.6by9.net/output-to-multiple-audio-devices-with-alsa/)
[*][http://alsa.opensrc.org/TwoCardsAsOne](http://alsa.opensrc.org/TwoCardsAsOne)
[*][http://alsa.opensrc.org/MultipleCards#Multiple_devices](http://alsa.opensrc.org/MultipleCards#Multiple_devices)
[/LIST]

---

