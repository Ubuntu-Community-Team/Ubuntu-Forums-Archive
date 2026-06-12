---
title: "no sound on fresh install of 17.10"
date: 2017-11-12
forum: Multimedia Software
---

### Post by mcmillanje on 2017-11-12
Fresh install 17.10 no sound whatsoever.

aplay -l shows outputs:

```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT1802 Analog [VT1802 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: VT1802 Alt Analog [VT1802 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I've tried basic troubleshooting but too new at this to really know what I'm doing. What steps should I take?

Here's my alsa info: [http://www.alsa-project.org/db/?f=dba596c44ab8277bdffec73d9989553740142b96]("http://www.alsa-project.org/db/?f=dba596c44ab8277bdffec73d9989553740142b96")

---

### Post by Yellow Pasque on 2017-11-12
I don't see anything obviously wrong in the info. If you have the correct output device selected in the volume control, sound should work on a fresh install. There's no excuse it for it not to work on a System76 system. I would contact them for support.

---

### Post by mcmillanje on 2017-11-12
Thanks for taking a look! I rebooted a few times and now it works...but if it happens again I'll reach out. Their support has always been great in the past.

---

