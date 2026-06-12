---
title: "Problem with Audio (HP series DV9500)"
date: 2009-07-27
forum: Multimedia Software
---

### Post by hyperAura on 2009-07-27
Hi.. sound wont be heard after upgrading from ubuntu 8.04 to 9.04.. 
The thing is that when i plug in my headphones, sound is playing through them but speakers are not working..

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci | grep Audio -i
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

i remeber about 2 years ago playing with alsamixer to fix it, but since then i formatted it and now i cannot recall anything from back then on how to fix this problem.. thnx in advance..

---

### Post by hyperAura on 2009-07-27
Problem is solved.. had to switch from PulseAudio Mixer to Alsa Mixer.. thnx anw

---

