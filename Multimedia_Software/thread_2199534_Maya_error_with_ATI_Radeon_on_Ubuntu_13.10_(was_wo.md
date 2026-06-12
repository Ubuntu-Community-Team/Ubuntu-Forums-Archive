---
title: "Maya error with ATI Radeon on Ubuntu 13.10 (was working fine on 13.04)"
date: 2014-01-14
forum: Multimedia Software
---

### Post by dmick on 2014-01-14
When trying to run Maya (2014, SP3) after upgrading from Ubuntu 13.04 to Ubuntu 13.10, i get the following error (sudo maya):

```

$ sudo su
# export LIBGL_DEBUG=verbose
# maya

libGL: AtiGetClientDriverName: 13.10.10 fglrx (screen 0)
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 16, (OK)
ukiGetBusid returned 'PCI:1:0:0'
ukiOpenDevice: node name is /dev/ati/card1
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card2
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card3
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card4
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card5
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card6
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card7
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card8
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card9
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card10
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card11
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card12
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card13
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card14
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiOpenDevice: node name is /dev/ati/card15
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: open result is -1, (No such device)
ukiOpenDevice: Open failed
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 16, (OK)
ukiOpenByBusid: ukiOpenMinor returns 16
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 17, (OK)
ukiOpenByBusid: ukiOpenMinor returns 17
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /root/.drirc: No such file or directory.
libGL error: failed to load driver: swrast
maya.bin: indirect_init.c:953: __glXNewIndirectAPI: Assertion `o > 0' failed.

maya encountered a fatal error

Signal: 6 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/root.20140114.1213.ma
Segmentation fault (core dumped)

```

I have spent hours on it and didn't find any solution. I tried the following as suggested from my research: 
```

export LIBGL_ALWAYS_INDIRECT=y

```
It still crashes but with a much shorter error message:
```

maya.bin: indirect_init.c:953: __glXNewIndirectAPI: Assertion `o > 0' failed.

maya encountered a fatal error

Signal: 6 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/root.20140114.1222.ma
Segmentation fault (core dumped)

```

It seems to be related to the graphic card drivers which have been updated during the upgrade but i have no clues why this is happening.

Below is the output of fglrxinfo if it's useful. Any help would be very much appreciated.
```

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7800 Series
OpenGL version string: 4.2.12337 Compatibility Profile Context 9.012 
```

---

