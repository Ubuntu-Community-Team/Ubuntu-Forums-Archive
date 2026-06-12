---
title: "PCTV PRO problem"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by arkoudi on 2006-10-23
Hi it's me again, I found out how to work it out with the bttv driver.
Everything is fine...if I do a dmesg | grep bttv I get

bttv: driver version 0.9.16 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
bttv0: Bt878 (rev 17) at 0000:00:0c.0, irq: 169, latency: 32, mmio: 0xf7008000
bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
bttv0: using: Pinnacle PCTV Studio/Rave [card=39,insmod option]
bttv0: gpio: en=00000000, out=00000000 in=00fffbff [init]
bttv0: i2c: checking for MSP34xx @ 0x80... found
bttv0: pinnacle/mt: id=2 info="PAL+SECAM / stereo" radio=yes
bttv0: using tuner=3
bttv0: i2c: checking for MSP34xx @ 0x80... found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: registered device radio0
bttv0: PLL: 28636363 => 35468950 . ok

after that...radio is finding frequencies but no sound...and the TV program can't find Tv Stations..
also the composite in of my Card is working perfect :/ any ideas? plz plz plz :)
With card=39 and tuner=3 I had no problem in suse 9 , 10.0, 10.1

---

### Post by arkoudi on 2006-10-24
anyone?

---

