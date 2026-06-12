---
title: "New 2.6.15-27-K7 Kernel kill audio"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by sportrider on 2006-09-20
When I used synaptic to update my kernel to 2.6.15-27 a couple days ago, my sound stopped working.

Book back into 2.6.15-26 and sound works again.

This from dmesg when I boot with 26
[17179602.256000] saa7134 ALSA driver for DMA sound loaded
[17179602.256000] saa7133[0]/alsa: saa7133[0] at 0xf1004000 irq 82 registered as card -1

I seem to get the same thing when booting the broken 27 kernel.  I'm not sure what else I can report that will help.
Sep 19 16:54:08 dogbert kernel: [17179602.780000] saa7134 ALSA driver for DMA sound loaded
Sep 19 16:54:08 dogbert kernel: [17179602.780000] saa7133[0]/alsa: saa7133[0] at 0xf1004000 irq 74 registered as card -1

---

