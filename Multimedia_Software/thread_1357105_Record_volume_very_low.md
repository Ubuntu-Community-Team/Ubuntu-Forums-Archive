---
title: "Record volume very low"
date: 2009-12-16
forum: Multimedia Software
---

### Post by amsterdamharu on 2009-12-16
When I talk into the microphone the sound comes out of my speakers but when I record using sound recorder, skype (test call) or audacity the sound volume is realy low.
Using Ubuntu 8.04

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

In /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz I could find:
    ALC662
      3stack-dig    3-stack (2-channel) with SPDIF
      3stack-6ch     3-stack (6-channel)
      3stack-6ch-dig 3-stack (6-channel) with SPDIF
      6stack-dig     6-stack with SPDIF
      lenovo-101e     Lenovo laptop
      eeepc-p701    ASUS Eeepc P701
      eeepc-ep20    ASUS Eeepc EP20
      auto        auto-config reading BIOS (default)

Edited /etc/modprobe.d/alsa-base and added the line:
options snd-hda-intel model=3stack-6ch

Rebooted and got the mic working but not when recording or using skype. All applications use HDA NVidia (Alsa mixer) and the properties of volume control is set to this.
As stated before when I set the volume of the mic higher I can hear what I say in the mic through my loudspeakers but it won't record.

Thanks for reading this.

---

### Post by Tclarkie on 2009-12-16
in terminal type alsamixer and then press cursor keys to get ove to MIC, turn in up by pressing up

---

### Post by amsterdamharu on 2009-12-16
Thanks for your reply but no, tried to set the mic to full volume with alsamixer (done it already in volume control) and as stated before I can hear the sound coming from the mic just fine through my loudspeakers.

When I try to record it or use it for skype the volume is really low though.

---

### Post by amsterdamharu on 2009-12-17
Not sure what fixed it, had a couple of reboots and switched back and forth with the 
options snd-hda-intel model=3stack-6ch
setting. Checked volume control and the mic wasn't muted but suddenly it's working. Must have overlooked something but I am happy it's working now.

---

