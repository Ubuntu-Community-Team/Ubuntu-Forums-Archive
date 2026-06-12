---
title: "USB Audio Interface not listed in unity-control-center output tab"
date: 2014-08-31
forum: Multimedia Software
---

### Post by adempewolff on 2014-08-31
I just upgraded to 14.04.  Previously in 12.04 I used a m-audio fastrack pro to play sound through my powered monitors.  Getting the input-side of this interface to work takes some tinkering (and thus I use a different customized version of Ubuntu Studio on another partition for this) but playback always worked fine without any tinkering.

Currently, the usb device is connected and ALSA sees the soundcard:

```
$ lsusb
Bus 002 Device 003: ID 04f2:b2b0 Chicony Electronics Co., Ltd Camera
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 0763:2012 Midiman M-Audio Fast Track Pro
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT1802 Analog [VT1802 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: VT1802 Alt Analog [VT1802 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

But it's not displayed as an output option in the unity-control-center sound settings panel.

I'm not particularly familiar with the unity-control-center or what it's using as a backend these days (pulseaudio still?), could anyone give some suggestions about how to continue troubleshooting this regression?

Thanks in advance for any help or suggestions!

---

### Post by mc4man on 2014-09-01
you could install pavucontrol & then open it. Maybe it'll have your usb listed..

---

