---
title: "Skype Sound Audio Recording and Microphone - 64 bit Karmic Koala"
date: 2010-03-22
forum: Multimedia Software
---

### Post by ProgressionMurph on 2010-03-22
Hello everyone,

My Skype Audio recording settings don't seem to work or I am not using the appropriate playback settings. My only Skype sound options are PulseAudio Server (local). Within my sound preferences (speaker icon>right click sound preferences) I can switch my connector between Microphone 1, Microphone 2, and Line in.

My OS is a 64bit Karmic Koala. My computer is a Fujitsu T5010.
This may be helpful:

```
alex@This-is:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
alex@This-is:~$
```

Any thoughts?

Thanks,
Alex

---

