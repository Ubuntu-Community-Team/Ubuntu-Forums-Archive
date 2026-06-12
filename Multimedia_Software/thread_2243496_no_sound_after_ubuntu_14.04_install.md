---
title: "no sound after ubuntu 14.04 install"
date: 2014-09-09
forum: Multimedia Software
---

### Post by kopplow on 2014-09-09
Hi,

after installing ubuntu 14.04 I get no sound at all. SOund in windows 8 (same machine) works ok.

I tried reinstalling, alsamixer to check if unmuted etc , nothing helps.

aplay -l gives me

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[http://www.alsa-project.org/db/?f=005dfaaa5f74b717886a862da21b5afe7679a13d](http://www.alsa-project.org/db/?f=005dfaaa5f74b717886a862da21b5afe7679a13d)

Anyone some hints what else to do to get it working ?

---

### Post by Yellow Pasque on 2014-09-10
```
Driver version:     k3.13.0-35-generic
Library version:    1.0.25
Utilities version:  1.0.27.2
```

You have an old version of ALSA library (libasound2). DId you upgrade from an older version of Ubuntu?

---

