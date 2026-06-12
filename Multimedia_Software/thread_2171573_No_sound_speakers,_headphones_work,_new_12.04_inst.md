---
title: "No sound speakers, headphones work, new 12.04 install"
date: 2013-08-31
forum: Multimedia Software
---

### Post by bfromcolo on 2013-08-31
I just installed 12.04 and ran update, my motherboard is an ASUS M5A97 R2.0.

I am not getting sound through the speakers connected to the motherboard I/O panel, but if I plug head phones into the front panel I do get sound.

With only speakers connect to the I/O panel, 3 sound devices are listed, although none work:
Digital Output (S/PDIF)
Analog Output
Headphones

When I plug headphones into the front panel only two devices are listed, the Analog Output does work properly:
Digital Output (S/PDIF)
Analog Output

This all worked fine with Windows so I do not think a hardware issue at fault here.

Any help would be appreciated, I have been searching for answer, but only found other posts describing similar problems with no solution.

Thanks

---

### Post by bfromcolo on 2013-08-31
To add additonal details, I relized that when I plug head phones into the front jack I am getting sound out of both the headphones and the speakers.

I tried creating a etc/asound.conf file buit this did not change what is happening.  I tried with card 0 device 0, and with card 0 device 1.

I am running the 313 NVIDIA drivers, but I am not using any sound output from the video card.


Output from aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Yellow Pasque on 2013-08-31
Can you give full alsa info?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by bfromcolo on 2013-08-31
Sure

[http://www.alsa-project.org/db/?f=517154d5dd54482ea13701153a56440d0a60d127](http://www.alsa-project.org/db/?f=517154d5dd54482ea13701153a56440d0a60d127)

Thanks for looking!

---

