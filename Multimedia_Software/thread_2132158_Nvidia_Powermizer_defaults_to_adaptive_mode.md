---
title: "Nvidia Powermizer defaults to adaptive mode?"
date: 2013-04-03
forum: Multimedia Software
---

### Post by Flash__Gordon on 2013-04-03
Has anyone been able to force "preferred Maximum Performance" in 12.04? 
Running 12.04.2 LTS with Geforce 7300 GT 512 MB

Any help would be appreciated.

Dave

---

### Post by wildmanne39 on 2013-04-03
Moved to own thread!

---

### Post by mc4man on 2013-04-04
The answer was in prior posts in thread you orig. posted in, did you read thru?

What I use here for a xorg.conf, max on ac, adaptive on battery
```
Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
EndSection

```

This would likely give max all the time, never used here

```
Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x1; PowerMizerDefaultAC=0x1"
EndSection

```

---

