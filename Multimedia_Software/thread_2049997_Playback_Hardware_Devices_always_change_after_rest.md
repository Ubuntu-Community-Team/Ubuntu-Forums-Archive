---
title: "Playback Hardware Devices always change after restart"
date: 2012-08-29
forum: Multimedia Software
---

### Post by serious7 on 2012-08-29
Hi,

When I restart my computer, my playback hardware devices always change after restarting the machine.

For example, when I type aplay -l, I will get the following output. 

```
harnek@harnek-OEM:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: STX [Xonar STX], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: STX [Xonar STX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

My target alsa device is  STX [Xonar STX], device 0: Multichannel and I would set it to 1,0 on my audio player. However, when I restart, it would often change to something completely random. How can I keep the card# and device# to be the same after every restart?

---

### Post by mrowth on 2012-08-31
You can add options to /etc/modprobe.d/alsa-base.conf to give fixed indices to specific devices and stop them from being switched around on bootup.

For example, I used ```
options snd-emu10k1 index=0
``` to give my Audigy 2 index 0, making it the default card.

As for how to find out which device name to use, I looked at the output of ```
lsmod | grep snd
``` and replaced underscores with hyphens... I don't know if that's the best way.

---

