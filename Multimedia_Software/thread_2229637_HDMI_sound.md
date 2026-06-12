---
title: "HDMI sound"
date: 2014-06-14
forum: Multimedia Software
---

### Post by impliedconsent2 on 2014-06-14
[LIST=1]
[*]```
aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
[*]I primarily use 0,0; however, there are times when I want bigger sound and watching it big screen.  This "USED" to work prior to 14.04LTS
[*]Testing some .wav (right, center, left .wavs), I found that 1,7 will produce sound just fine; however, I don't want to use it permanently (asound.conf), just be able to switch back and forth.
[/LIST]


**.... err .... DISREGARD! ** Embarrassingly sometimes the simplest is the easiest.  VLC was sitting on Audio-->Audio Device-->Built-In Audio... my bad ... go back to what you were doing (keeping this posted because sometimes we forget the simplest things).:redface:

---

