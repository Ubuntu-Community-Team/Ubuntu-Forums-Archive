---
title: "[SOLVED] Strangeness with 4-port capture card and v4l."
date: 2008-05-19
forum: Multimedia Software
---

### Post by Gordon Bennett on 2008-05-19
(Ubuntu 8.04)

I have a Kodicom 4400R clone and have the driver loading with this configuration:

```
alias char-major-81 bttv
options bttv gbuffers=16 card=133,132,133,133 tuner=4,4,4,4
```

Dmesg is returning:

```
[   56.016425] bttv: driver version 0.9.17 loaded
[   56.016428] bttv: using 16 buffers with 2080k (520 pages) each for capture
[   56.016470] bttv: Bt8xx card found (0).
[   56.016698] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   56.016705] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   56.016714] bttv0: Bt878 (rev 17) at 0000:02:0c.0, irq: 19, latency: 32, mmio: 0xfdfff000
[   56.016957] bttv0: using: Kodicom 4400R (slave) [card=133,insmod option]
[   56.016982] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   56.017495] bttv0: tuner absent
[   56.017513] bttv0: registered device video0
[   56.017529] bttv0: registered device vbi0
[   56.017545] bttv0: PLL: 28636363 => 35468950 .. ok
[   56.047878] bttv: Bt8xx card found (1).
```

Looks ok...

But, the strange thing is that I get a mostly blue screen unless I populate what's coming in; so, for example, if I point the camera at a dark spot, the signal coming into xawtv is mostly blue (= no signal) - however, if I point it at a bright source, I get less of the blue and more of what I am filming!  Am I missing some strange configuration or is something more sinister going on, like missed sync signals?

Also, is this normal:

v4l2: WARNING: framebuffer size mismatch
v4l2: me=1280x960 v4l=**0x0**

v4l2 reporting **0x0**?  It doesn't seem right...

Regards.

EDIT:  Solved - will post the findings in the 4400 howto.

---

