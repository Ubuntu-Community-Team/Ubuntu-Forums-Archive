---
title: "Using PCTV 110i"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by gnarula on 2006-11-05
I have a Pinnacle PCTV 110i tv-tuner card and have got the windows drivers for it... How do i install the drivers in ubuntu and how do i configure it?? Have searched Pinnacle's site for drivers but found nothing..

Help pls.

Gaurav

---

### Post by Kropotkin on 2006-11-17
If you are using Edgy or Dapper, the kernel module is probably included in the distro, and you won't need additional files. Plug the card in, reboot, and look at dmesg or /var/log/kern.log. If the kernel recognizes the card, you'll see some lines like this:

```
saa7130/34: v4l2 driver version 0.2.14 loaded
saa7133[0]: found at 0000:02:0b.0, rev: 208, irq: 193, latency: 64, mmio: 0xfeaf9800
saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 40i/50i/110i (saa7133) [card=77,autodetected]
saa7133[0]: board init: gpio is 200e000
ir-kbd-i2c: Pinnacle PCTV detected at i2c-1/1-0047/ir0 [saa7133[0]]
```

(this is what is displayed for my pinnacle card)

HTH

---

