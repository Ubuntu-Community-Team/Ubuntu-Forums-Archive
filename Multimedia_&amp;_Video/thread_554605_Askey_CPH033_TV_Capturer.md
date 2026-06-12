---
title: "Askey CPH033 TV Capturer"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by kula on 2007-09-19
I've got a lot of problems with this gear. Typical kernel doesn't recognize what this equipment is, so I have to load proper krenel modules by my self and I'm sure on 99% they're ok. But when I'm starting TvTime I've got NO SIGNAL, and I don't know why. When I'm scanning video devices by 
```
$ xawtv -hwscan
  /dev/video0: OK                         [ -device /dev/video0 ]
      type : v4l2
      name : BT848A video (Askey CPH03x TV C
      flags: overlay capture tuner
```
it looks ok, dmesg 
```
[15091.605987] Linux video capture interface: v2.00
[15091.667529] bttv: driver version 0.9.16 loaded
[15091.667537] bttv: using 8 buffers with 2080k (520 pages) each for capture
[15091.667885] bttv: Bt8xx card found (0).
[15091.667993] bttv0: Bt848 (rev 18) at 0000:00:0b.0, irq: 21, latency: 32, mmio: 0xe2000000
[15091.668189] bttv0: using: Askey CPH03x TV Capturer [card=59,insmod option]
[15091.668390] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[15091.675105] bttv0: using tuner=16
[15091.675187] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[15091.676005] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[15091.676837] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[15091.677674] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[15091.697168] tuner 1-0060: All bytes are equal. It is not a TEA5767
[15091.697176] tuner 1-0060: chip found @ 0xc0 (bt848 #0 [sw])
[15091.697221] tuner 1-0060: type set to 16 (Temic PAL_DK (4016 FY5))
[15091.697226] tuner 1-0060: type set to 16 (Temic PAL_DK (4016 FY5))
[15091.697403] tuner 1-0061: chip found @ 0xc2 (bt848 #0 [sw])
[15091.708173] bttv0: registered device video0
[15091.708285] bttv0: registered device vbi0
[15091.708398] bttv0: PLL: 28636363 => 35468950 . ok

```
looks ok too, so where ist the problem?

---

