---
title: "GStreamer unable to detect any sound devices"
date: 2017-04-06
forum: Multimedia Software
---

### Post by Rick St. George on 2017-04-06
Upon adding "Audio Mixer" to the Panel, Get this Error:
> 
GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem.




MY SOUND:

Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)

ALSO (but not enabled):
Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)

CODE OUTPUT:

```

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


PulseAudio works to control sound input/output. But would like the "audio" icon on the panel as shortcut to access audio control. 

Any suggestions?
Thanks!
Rick

):P

---

### Post by Rick St. George on 2017-10-16
After adding "indicator plugin" found Sound Menu. That added the "speaker icon" which accesses Volume Control and Configuration of Audio.

---

