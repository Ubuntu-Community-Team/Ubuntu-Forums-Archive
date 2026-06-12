---
title: "Stuttering audio in Jaunty"
date: 2009-09-03
forum: Multimedia Software
---

### Post by Scienceman123 on 2009-09-03
Applications: All
When: Randomly
Hardware: Toshiba Satellite A105-S2051
Aplay output:
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Sound on my laptop beings stuttering at random times, and is not fixed without a reboot. Restarting pulse or using alsa force-reload fail to solve the problem. Logs and dmesg show nothing unusual. This occurs in all applications with no particular pattern.

---

### Post by kostkon on 2009-09-03
Try lowering the PCM volume level a little.

---

### Post by Scienceman123 on 2009-09-07
That did not help. The issue is not stuttering at all times, but at random with no apparent cause.

---

