---
title: "Exciting! Where does my IEC958 hide?"
date: 2010-02-07
forum: Multimedia Software
---

### Post by Pagnol on 2010-02-07
Hi,

according to aplay -l my computer (a Dell Dimension 5000) should have an IEC958:

[PHP]**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
[/PHP]

But where? There's nothing on the backside of the computer nor on front, I cannot find SPDIF on the mainboard itself either. What's wrong?

I GREATELY appreciate your help! :D

---

### Post by markbuntu on 2010-02-07
IEC958 is on the ICH6 chip but dell decided to not use it is the most likely explanation. The alsa driver cannot tell that.

---

