---
title: "[WINTV HVR-4000]cx22702_readreg error after suspend"
date: 2013-09-24
forum: Mythbuntu
---

### Post by LastStarDust on 2013-09-24
Hello,
I'm experiencing some trouble with a tv card I bought recently.
Model is [Hauppauge WinTV-HVR-4000]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000") and before buying I double checked the card was compatible with linux.
Indeed the card works almost flawlessly. The only problem pops up when I resume after suspending/hibernating.
The card ceases to work and in /var/log/kern.log appears a lot of error messages.

```
Sep 24 23:28:24 zion kernel: [ 8856.997873] tda9887 0-0043: i2c i/o error: rc == -6 (should be 4)
Sep 24 23:28:24 zion kernel: [ 8856.999435] cx22702_readreg: error (reg == 0x0d, ret == -6)
Sep 24 23:28:24 zion kernel: [ 8857.000192] cx22702_writereg: error (reg == 0x0d, val == 0x01, ret == -6)
Sep 24 23:28:24 zion kernel: [ 8857.029626] cx22702_readreg: error (reg == 0x0a, ret == -6)
Sep 24 23:28:24 zion kernel: [ 8857.030384] cx22702_readreg: error (reg == 0x23, ret == -6)
Sep 24 23:28:24 zion kernel: [ 8857.031186] cx22702_readreg: error (reg == 0x23, ret == -6)
...

```

tda9987 errors are only few but cx22702 errors are about one hundred per sec (I'm not exaggerating).

I plugged the card in two pcs and tested it with several kernels and drivers. These are systems showing errors:
[LIST]
[*]Ubuntu 10.04 x86 - kernel 2.6.32 - firmware 1.26.90.0 - ubuntu default driver
[*]Ubuntu 12.04 x86 - kernel 3.8.0-44 - firmware 1.26.90.0 - ubuntu default driver
[*]Ubuntu 12.04 x86 - kernel 3.8.0-44 - firmware 1.26.90.0 - [LinuxTV V4L-DVB driver]("http://git.linuxtv.org/media_build.git")
[*]Ubuntu 12.04 x64 - kernel 3.2.0-53 - firmware 1.26.90.0 - ubuntu default driver
[*]I've performed also other tests but these are the only ones I can remember by heart.
[/LIST]

If you use default drivers and firmware errors don't show up. But mythtv doesn't work with default firmware ...
I stress: card works after a fresh boot. It is suspend/resume that breaks something down.
I tried to unload the module (modprobe -r cx22702) before hibernating and reload afterwards without any positive effect.

---

### Post by LastStarDust on 2013-09-24
I tried all firmwares listed here without succeeding: [Hauppauge WinTV-HVR-4000]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000")
Some links are even broken ...

---

