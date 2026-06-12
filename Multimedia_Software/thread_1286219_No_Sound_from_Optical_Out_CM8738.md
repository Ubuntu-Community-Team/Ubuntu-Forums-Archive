---
title: "No Sound from Optical Out CM8738"
date: 2009-10-08
forum: Multimedia Software
---

### Post by KyleBrandt on 2009-10-08
I installed a new sound card, a Turtle Beach card, and can't seem to get sound out of the optical out.  lspci says it is a CM8738 chip.  I can get static out the front two channels with the following command but that is it so far (when the test says center, nothing works):

```
 speaker-test -Dplug:iec958 -c 6
```

When sound does come out those two channels, my reciever says PCM, but when the test says other channels, it says NO AUDIO INPUT.  I disable the onboard intel audio from the bios.

aplay -l says:
```
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


Currently I have the following switches checked:
IEC958 5V
IEC958 Output

I also tried:
asoundconf set-default-card CMI8738 

I don't really know very much about sound trouble shooting, so any help is appreciated. I am using Ubuntu 9.04

---

### Post by rtalcott on 2009-10-08
Digital is not muted...and I cannot get anything out either...

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

rt

---

### Post by rtalcott on 2009-10-08
This worked for me in the past but not now.
[http://ubuntuforums.org/printthread.php?t=776958](http://ubuntuforums.org/printthread.php?t=776958)
rt

---

### Post by KyleBrandt on 2009-10-08
If I uninstall pulse, I get it working okay with xbmc, but nothng else...

---

### Post by rtalcott on 2009-10-09
Digital Output is NOT muted...I can see volume on the PA Volume Control...but no lock on my external DAC which does work...no optical or coax signal...

I have an eVga mobo with a nVidia chipset and spdif works fine....this machine...an ecs...has analog working but no digital.
rt

---

