---
title: "Error when launching maya"
date: 2010-12-20
forum: Multimedia Software
---

### Post by raylistic87 on 2010-12-20
Hi all, I faced this error today when I tried launching my maya.
Anyone know how to overcome this? I have tried reinstalling the nvidia-settings and it does not help. Thanks.

```
maya encountered a fatal error

Signal: 11 (Unknown Signal)
Stack trace:
  /lib/libc.so.6(+0x33c20) [0x7f5a006dbc20]
  TinputDeviceManager::deviceByIndex(short) const
  Twindow::unStow(Tevent const&)
  TstartupWnd::unStow(Tevent const&)
  /usr/autodesk/maya2009-x64/bin/maya.bin() [0x414f2d]
  /usr/autodesk/maya2009-x64/bin/maya.bin() [0x412ec2]
  /usr/autodesk/maya2009-x64/bin/maya.bin() [0x41058a]
  /usr/autodesk/maya2009-x64/bin/maya.bin() [0x41e93b]
  __libc_start_main
  __gxx_personality_v0
```

---

