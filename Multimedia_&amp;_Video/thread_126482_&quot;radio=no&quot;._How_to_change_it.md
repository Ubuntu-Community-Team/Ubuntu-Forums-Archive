---
title: "&quot;radio=no&quot;. How to change it ?"
date: 2006-02-06
forum: Multimedia &amp; Video
---

### Post by fred77 on 2006-02-06
Hello, 

I have got a Pinacle card with a bt878 chipset. I installed gnomeradio but it does not work as it needs a /dev/radio which is missing (I don't have neither /dev/radio0). So, here is what dmes |grep bttv returns:

[4294710.886000] bttv: driver version 0.9.15 loaded
[4294710.886000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294710.886000] bttv: Host bridge needs ETBF enabled.
[4294710.891000] bttv: Bt8xx card found (0).
[4294710.892000] bttv0: Bt878 (rev 17) at 0000:00:12.0, irq: 5, latency: 64, mmio: 0xebdfe000
[4294710.892000] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[4294710.892000] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[4294710.892000] bttv0: enabling ETBF (430FX/VP3 compatibilty)
[4294710.892000] bttv0: gpio: en=00000000, out=00000000 in=00ff63ff [init]
[4294710.945000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294710.947000] bttv0: miro: id=24 tuner=3 radio=[COLOR="Red"]no[/COLOR] stereo=no
[4294710.947000] bttv0: using tuner=3
[4294710.947000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294710.949000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294710.952000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294710.954000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294711.137000] bttv0: registered device video0
[4294711.140000] bttv0: registered device vbi0
[4294711.140000] bttv0: PLL: 28636363 => 35468950 .. ok

Does someone know how to change this value to "yes" ?

Thank you,

Frédéric

---

