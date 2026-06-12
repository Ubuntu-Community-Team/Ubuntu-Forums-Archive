---
title: "Flash mutes HDMI audio out"
date: 2016-04-09
forum: Multimedia Software
---

### Post by Klaus_A_Schmid on 2016-04-09
*4.4.0.18 - Xenial 16.04 x64 on Asus Zenbook*

Video and Audio output via HDMI works fine until I open flash video playback.
In this case, the computer seems to turn into a muted mode where not even the "sound test" can be heard anymore, as well as any other sound that worked fine before.
PulseAudio Volume Control still displays the audio output (volume going up and down). Selected mode is HDMI Stereo.
A restart of the TV does not work.

As soon as the window with flash player is closed again, audio returns to normal.

aplay -l outputs:
```
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

