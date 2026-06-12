---
title: "Getting no audio"
date: 2009-11-07
forum: Multimedia Software
---

### Post by backfour94 on 2009-11-07
Hi my sound is working fine on Windows XP.

It was working fine on 8.n of Ubuntu.

It isn't working at all on 9.n (have upgraded to 9.10 and it still isn't working).

When the system starts the sound is muted but increasing the volume doesn't make any difference.

Not sure where I need to look so any help is appreciated.

---

### Post by backfour94 on 2009-11-08
Don't know if this helps; it's the response to the aplay -l command (no idea what it means but I found it on another post):

steve@mesh:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738_1 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CMI8738_1 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738_1 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
steve@mesh:~$

---

### Post by marc.verwerft on 2009-11-08
You can find a very helpfull guide here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Regards,

Marc

---

