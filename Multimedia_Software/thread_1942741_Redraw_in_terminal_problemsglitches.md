---
title: "Redraw in terminal problems/glitches"
date: 2012-03-18
forum: Multimedia Software
---

### Post by aneganov on 2012-03-18
Hi all,

I'm on Ubuntu 11.10 and having problems with terminal applications like Midnight Commander - when it redraws the screen, its not actually updated, so I have to press Ctrl-L everytime to get it really redrawn.

Any ideas what could be wrong?

lspci:

```
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
```

uname -a:

```
Linux alpha 3.0.0-16-server #29-Ubuntu SMP Tue Feb 14 13:08:12 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

from Xorg log:

```
[  5499.170] (II) LoadModule: "nvidia"
[  5499.170] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  5499.170] (II) Module nvidia: vendor="NVIDIA Corporation"
[  5499.170] 	compiled for 4.0.2, module version = 1.0.0
[  5499.170] 	Module class: X.Org Video Driver

```

---

