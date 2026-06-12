---
title: "Black screen after installing fglrx"
date: 2014-01-27
forum: Multimedia Software
---

### Post by jaspervdmaarel on 2014-01-27
Hi guys,

I am running Ubuntu 13.10 on my PC with 2x Sapphire Radeon HD 7950. After I installed fglrx, ran ```
sudo aticonfig --adapter=all --initial
``` and rebooted, I get a black screen.

When I go into recovery mode and run fglrxinfo, it gives me the following output:
```
unable to open display (null)
```

When I looked on the ubuntu forums someone suggested I run ```
aticonfig --acpi-services=off
``` but unfortunately this doesnt seem to have any effect.

Does anyone have some suggestion? Any help would be appreciated, and I would be happy to provide more information if needed.

Thanks in advance!

EDIT:
I should also mention that I previously had an install with fglrx on this system which worked fine. At some point this black screen appeared. After that I decided to reinstall Ubuntu, which works fine until I install fglrx again.

---

### Post by darran-kelinske on 2014-09-18
I'm having a similar issue on 14.04/10 with the latest packages. Did you find a fix for this?

---

### Post by arun-3 on 2014-09-18
Me too having the same issue in ubuntu 14.4 LTS,If you find a fix means tell me?

---

