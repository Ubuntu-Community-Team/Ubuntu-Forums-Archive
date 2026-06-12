---
title: "alsa mixer need to load module-detect manually"
date: 2010-09-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yumi on 2010-09-18
Since a while now I have to manually load 
```
$ pactl load-module module-detect
```
every time I boot the computer. Otherwise the sound applet does not find an input or output device and - no sound.

How can I load module detect automatically, or why does this not happen during the boot process?

---

### Post by ktp on 2010-09-18
did you try adding it to  /etc/pulse/default.pa

---

### Post by Yumi on 2010-09-19
Thanks. I found the following and blocked the if construct. Now the sound is blowing Bavarian Beer festival umpa music out of the speakers. :) But - 

now System - Preferences - Sound brings up the message "Waiting for the sound system to respond" :(


```
### Automatically load driver modules depending on the hardware available
######.ifexists module-udev-detect.so
######load-module module-udev-detect tsched=0
######.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
#####.endif
```

---

