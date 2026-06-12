---
title: "Tv Card"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by christooss on 2006-07-11
I have one big problem. I have tv tuner. And I would like to make it work.

When I start my computer I get this out put when performin 
```

dmesg |grep bttv
```

```

[17179596.012000] bttv: driver version 0.9.16 loaded
[17179596.012000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179596.012000] bttv: Bt8xx card found (0).
[17179596.012000] bttv0: Bt848 (rev 18) at 0000:02:02.0, irq: 201, latency: 32, mmio: 0xe6000000
[17179596.012000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[17179596.012000] bttv0: gpio: en=00000000, out=00000000 in=00e707df [init]
[17179596.016000] bttv0: using tuner=-1
[17179596.016000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[17179596.404000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179596.408000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179596.412000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179596.412000] bttv0: registered device video0
[17179596.412000] bttv0: registered device vbi0

```

Then I do
```
sudo rmmod bttv
```
and
```
sudo modprobe bttv card=39 tuner=3
```

And I get this output whe dmesg


```
[17180053.592000] bttv: driver version 0.9.16 loaded
[17180053.592000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17180053.592000] bttv: Bt8xx card found (0).
[17180053.592000] bttv0: Bt848 (rev 18) at 0000:02:02.0, irq: 201, latency: 32, mmio: 0xe6000000
[17180053.592000] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,insmod option]
[17180053.592000] bttv0: gpio: en=00000000, out=00000000 in=00e707df [init]
[17180053.716000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[17180053.716000] bttv0: miro: id=1 tuner=0 radio=matchbox stereo=yes
[17180053.716000] bttv0: using tuner=3
[17180053.716000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[17180053.736000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17180053.740000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17180053.744000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17180053.772000] bttv0: registered device video0
[17180053.772000] bttv0: registered device vbi0
[17180053.772000] bttv0: registered device radio0
[17180053.800000] bttv0: PLL: 28636363 => 35468950 ..........failed
```

Please help What can I do. Cause tvtime-scanner and scantv doesn't find anything but antenna is working properly

---

