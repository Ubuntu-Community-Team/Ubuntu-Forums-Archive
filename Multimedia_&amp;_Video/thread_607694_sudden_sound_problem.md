---
title: "sudden sound problem"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by kernel1 on 2007-11-09
Suddenly I have no sound when I logged in ubuntu. (version 7.04)
 I tried to follow solutions from similar topics and I typed in shell:

> sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
sudo reboot

After rebooting the sound has not fixed.

aplay -l gives:

> **** List of PLAYBACK Hardware Devices ****
card 0: A5451 [ALI 5451], device 0: ALI 5451 [ALI 5451]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
....
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31

---

### Post by kernel1 on 2007-11-10
Anyone?

---

