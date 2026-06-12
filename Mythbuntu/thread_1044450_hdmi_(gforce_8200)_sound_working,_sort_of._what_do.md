---
title: "hdmi (gforce 8200) sound working, sort of. what does this mean ?"
date: 2009-01-19
forum: Mythbuntu
---

### Post by jeremycobert on 2009-01-19
hey guys, im running a gforce 8200 MB with the latest 177 restricted drivers. i upgraded the alsa drivers and can now see the HDMI card as
```

mythbox:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

at that point i was still not getting any audio playback until i found this command and then i heard the test.wav


```
mplayer -ao alsa:device=hdmi -ac hwac3,hwdts, test.wav
```

so i know that the sound can work in hdmi to my TV, i just need to know what i did with that command and what i should use in mythTV's audio setup. 

any help is much appreciated ! im so close now, yet so far.

---

