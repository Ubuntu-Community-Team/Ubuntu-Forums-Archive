---
title: "No sound"
date: 2013-08-11
forum: Multimedia Software
---

### Post by Alxl on 2013-08-11
Using Ubuntu 13.04 and have no sound.
I have tried various 'remedies' as I found them suggested and by now things must be well damaged.
Hope somebody can help

---

### Post by SweetAurora on 2013-08-11
Do you know what soundcard you have? Put this in a terminal and post here what it says.
```
aplay -l
```

---

### Post by Alxl on 2013-08-11
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by SweetAurora on 2013-08-11
I see some issues with the card, but lets try this first in terminal.
```
alsamixer
```
First push F5 then use the left and right arrow keys to go through the sliders. Look for PCM Master and Front. Make sure all three are turned all the way up. Then push escape to exit.

---

### Post by Alxl on 2013-08-11
alsamixer did it. PCM was set at MM and I had to change it  to 00.
Not everything is fine but at lease there is sound now.
Thank you!

---

