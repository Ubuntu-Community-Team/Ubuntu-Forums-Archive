---
title: "ATI IXP IEC958/SPDI output"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by okeefferd on 2007-11-04
I have analog audio working perfectly but would like to use SPDIF optical audio as I want to play some highdef files and dvds from this machine.  I have enabled the IEC958 option and made sure the volumes are turned on and up for the corresponding channels.  I have also made sure that MPlayer and VLC were using the correct device and were using the IEC958 port (hw 0.1 in my case) but i still get nothing.  When I test the device I dont hear anything and it doesnt look like the optical is even on when I look into the output port (no light).  Any ideas?  I'l post some debug stuff below.  Thanks.

alsa - l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Running Gutsy, Updated 11/4/07

---

