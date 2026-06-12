---
title: "DD over Onboard S/PDIF Out (Coax) does not work"
date: 2010-06-18
forum: Multimedia Software
---

### Post by Norbert42 on 2010-06-18
Hi,

I try to get dolby digital 5.1  (AC3)  sound out of my coaxial S/PDIF connector on my mainboard. After a lot of reading and trying I managed to get it to work using the following methods
```
ac3dec -C test.ac3
mplayer -ac hwac3 -ao alsa:device=hw=0.1  test.ac3
mplayer -ac hwac3 -ao alsa:device=hw=0.1  dolbytrain.vob
``` my Onkyo TS-SR508 reports Dolby Digital 5.1
All other methods I tried using totem, vlc and so on will only bring PCM stereo sound to my speakers.

gnome-volume-control only offers me stuff like:
```
Digital Stereo Duplex (IEC958) Digital Stereo (IEC958) Output + ... Input 
Analog Surround 5.1 Output + ... Input 
```aplay -L prints:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``` Any idea, what is causing this problem? Anything I can check or report?

Thanks for your help
Norbert

---

