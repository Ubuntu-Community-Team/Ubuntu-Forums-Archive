---
title: "ATI TV Wonder Help"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by antisolutions on 2006-10-04
Hi I have an ATI TV Wonder card (not pro, elite or anything, just the normal PCI one) that I'm trying to get working. Following the advice on the web, I've tried changing the tuner from the default of 17 to 2 as follows:

sudo rmmod bt878 bttv tuner
sudo modprobe bttv tuner=2 && sudo modprobe bt878

Following this my picture is better than before, but still unwatchable. The card works fine under Windows. Any advice would be appreciated. The output from dmesg is as follows:

[17223992.408000] bttv: driver version 0.9.16 loaded
[17223992.412000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17223992.412000] bttv: Bt8xx card found (0).
[17223992.412000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 177, latency: 32, mmio: 0xed105000
[17223992.412000] bttv0: detected: ATI TV Wonder [card=63], PCI subsystem ID is 1002:0001
[17223992.412000] bttv0: using: ATI TV-Wonder [card=63,autodetected]
[17223992.412000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[17223992.496000] bttv0: using tuner=2
[17223992.496000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[17223992.504000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17223992.508000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17223992.508000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17223992.544000] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[17223992.576000] bttv0: registered device video0
[17223992.576000] bttv0: registered device vbi0
[17223992.620000] bttv0: PLL: 28636363 => 35468950 .. ok
[17223992.784000] bt878: AUDIO driver version 0.0.0 loaded
[17223992.784000] bt878: Bt878 AUDIO function found (0).
[17223992.784000] bt878(0): Bt878 (rev 17) at 00:09.1, irq: 177, latency: 32, memory: 0xed106000
[17224002.560000] bttv0: PLL can sleep, using XTAL (28636363).

---

