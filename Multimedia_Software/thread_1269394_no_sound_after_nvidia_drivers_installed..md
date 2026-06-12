---
title: "no sound after nvidia drivers installed."
date: 2009-09-18
forum: Multimedia Software
---

### Post by bigjoe7 on 2009-09-18
Hi,

I installed unbuntu 9.04 vanilla last night and noticed that after I had installed Nvidia version 180 drivers my sound stopped working.  The sound was definitely working prior to driver installation.

Uninstalled the drivers and after a reboot sound returned.  The same issue occurred when installing version 173 driver set.

Hardware.

Nvidia 8500 GT
Mothreboard – Asus p5b deluxe
Onboard sound.

adrian@adrian-desktop:~$ aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
``` 

Performed a fuill update to the OS and the sound still will not work when Nvidia drivers applied.

Any thoughts?

---

### Post by bigjoe7 on 2009-09-18
Solved.

Swapped the Nvidia card out.

---

