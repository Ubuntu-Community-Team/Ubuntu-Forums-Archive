---
title: "Audio mutes on its own"
date: 2010-03-12
forum: Multimedia Software
---

### Post by Thomas Kenobi on 2010-03-12
I have a little problem with audio in Jaunty. Specifically every time I launch an application that features audio playback (decibel audio player, firefox on youtube) sound output auto-mutes. Getting sound back is as simple as pressing the mute button on my keyboard, but it's still a curious issue.

Unfortunately I can't provide many more details about the issue, as I hadn't logged in Ubuntu for a couple of weeks, so when I finally did, it downloaded a bunch of updates at once and any one of those could be responsible for this change in behaviour. I'm posting this here in case it rings any bells.

edit: The problem appears to exhibit varied behaviour for various applications. e.g.:
Firefox: I need to un-mute once and then it appears to work normally, even if I restart the application.
Decibel: Need to un-mute once every time I launch it and if I pause playback for more than a few minutes.
Totem Movie Player: Need to un-mute every time I pause playback for more than a few seconds.

---

### Post by Thomas Kenobi on 2010-04-28
*BUMP*

Any ideas?
The problem has persisted since March and I can't even begin to think how to fix this.

---

### Post by Thomas Kenobi on 2010-04-28
```
uname -a

Linux home-pc01-main 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

``````
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1828S Analog [VT1828S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1828S Digital [VT1828S Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
``````
cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Feb  8 2010 for kernel 2.6.31-20-generic (SMP).
``````
head -n 1 /proc/asound/card*/codec#*

Codec: VIA VT1828S
```

---

### Post by Thomas Kenobi on 2010-04-28
Ok, I just tried purging and then reinstalling the alsa and pulseaudio packages to reset configuration files. In addition I set my driver settings from "analog stereo duplex" to "Analog Surround 5.1 Output and Stereo Input". That seemed to temporarily fix things for Decibel and Totem, but not Firefox and Skype.

Note: Now they are all showing the problem again.

---

