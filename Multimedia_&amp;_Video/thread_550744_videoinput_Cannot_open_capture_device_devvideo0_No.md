---
title: "videoinput: Cannot open capture device /dev/video0: No such file"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by aldeby on 2007-09-14
when I try executing TvTime I get this output: ```
videoinput: Cannot open capture device /dev/video0: No such file
```
in fact in /dev I cannot find any video0 or video1 file/device! 
Why?

I have a cx23885 express card tv tuner by hauppauge, it is not specifically supported, however the cx23885 driver loads well (as far as I know from dmesg):
```
[   27.354465] CORE cx23885[0]: subsystem: 0070:7717, board: UNKNOWN/GENERIC [card=0,autodetected]
[   27.454723] cx23885[0]: i2c bus 0 registered
[   27.454820] cx23885[0]: i2c bus 1 registered
[   27.454920] cx23885[0]: i2c bus 2 registered
[   27.482755] cx23885[0]/0: found at 0000:04:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xf4000000

```
How can I make /dev/video0 appear? (I don't think touch command will do the job...) 
As far as I know in /dev directory devices links should be listed in any case, although when hardware device is not attached links are broken.

Thankyou

---

