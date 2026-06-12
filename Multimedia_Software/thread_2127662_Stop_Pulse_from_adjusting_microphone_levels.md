---
title: "Stop Pulse from adjusting microphone levels"
date: 2013-03-20
forum: Multimedia Software
---

### Post by freek_zero on 2013-03-20
Every time an app accesses the mic, or when I adjust the mic level within system settings, the mic levels (as reported by alsa) change. Boost goes way up, capture goes way down. I can only assume pulse is triggering this. How do I stop this?

Note this is not the usual Skype or Google Talk issue. This happens with all apps: Skype (with auto adjust unchecked), SFLPhone, sound recorder, even just opening Sound Settings from the system menu and adjusting mic level with the slider. I'll correct the levels with alsamixer but as soon as any of the aforementioned triggers are encountered, the levels get buggered again. I'm also having issues with random but generally long delays (up to 30s) before the mic starts working on incoming SFL or Skype calls.

An hour of searching has come up blank on both issues.

Help?

---

### Post by tgalati4 on 2013-03-20
What is the sound hardware that you are using?

```
aplay -l
```

---

### Post by freek_zero on 2013-03-21
Pretty standard on-board sound. Using plain jane analog mic.

card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by freek_zero on 2013-03-22
No-one else have this issue?

---

