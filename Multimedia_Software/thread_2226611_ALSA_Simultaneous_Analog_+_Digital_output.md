---
title: "ALSA Simultaneous Analog + Digital output?"
date: 2014-05-28
forum: Multimedia Software
---

### Post by djfake2 on 2014-05-28
How do I set ALSA up to output audio simultaneously from both analog and digital outputs on the same sound card? I am using a clean install of 14.04 LTS.

If I use System Settings > Sound, I can select one or the other. If I install paprefs (PULSE) and use the simultaneous box, it allows HDMI + Analog, but what I want is Optical + Analog, which are on the SAME sound card, the REALTEK ALC892. Here's aplay -l: 

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

NB: If I install Gnome ALSA Mixer, I can click and choose ICE958 and ICE958 Default PCM and  I get simultaneous output, but this does not survive on reboot. Thank you. 

[IMG]http://itjerk.files.wordpress.com/2014/05/screenshot-from-2014-05-26-081103.png[/IMG]

---

