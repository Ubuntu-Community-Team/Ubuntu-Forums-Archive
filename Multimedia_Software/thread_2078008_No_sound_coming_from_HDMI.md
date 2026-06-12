---
title: "No sound coming from HDMI"
date: 2012-10-29
forum: Multimedia Software
---

### Post by cypwrx on 2012-10-29
Good afternoon all! 

Having some issues getting sound to work in Ubuntu 12.04 x64. 

I have used the fglrx ATI driver (ATI Radeon 4350). 

Within Pulse audio control I am able to see the device listed, however, when I go into sound settings, there is no device listed. If I disable the HDMI device from pulseaudio, dummy audio then appears in the sound settings. 

If I run aplay -l I get the following 
> 
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  subdevices:1/1
  subdevice #0: subdevice #0


If I run alsamixer, it states:
> 
Card:  HDA ATI AMD
Chip: ATI 86xx HDMI
Item S/PDIF
(no volume control.. either mute or unmute)

If anyone could help I would appreciate it. This is a fresh build! let me know if I can run anything to help diagnose it.

---

