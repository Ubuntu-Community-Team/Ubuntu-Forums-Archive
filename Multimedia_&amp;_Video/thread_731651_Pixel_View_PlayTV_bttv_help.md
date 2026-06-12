---
title: "Pixel View PlayTV bttv help"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by shadow-of-sin on 2008-03-22
I've been trying to setup my Pixel View PlayTV card using BTTV 

However, my card does not seem to be recognized as when I type in:
```
lspci
```
there is no reference to my capture card.

Also, the dmesg output shows that the BTTV driver is loaded but that's it. i.e it only displays the following:
```

[46169.233037] bttv: driver version 0.9.17 loaded
[46169.233041] bttv: using 8 buffers with 2080k (520 pages) each for capture

```
rather than something like the following (as found in this thread: [http://ubuntuforums.org/showthread.php?t=584841](http://ubuntuforums.org/showthread.php?t=584841) ):
```
[ 2879.663485] bttv: Bt8xx card found (0).
[ 2879.663501] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 21, latency: 32, mmio: 0xdc7fe000
[ 2879.663516] bttv0: detected: Prolink Pixelview PV-BT [card=72], PCI subsystem ID is 1554:4011
[ 2879.663522] bttv0: using: Prolink Pixelview PV-BT878P+9B (PlayTV Pro rev.9B FM+NICAM) [card=72,insmod option]
[ 2879.663554] bttv0: gpio: en=00000000, out=00000000 in=006fd8ff [init]
[ 2879.669661] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[ 2879.670716] tuner 0-0063: chip found @ 0xc6 (bt878 #0 [sw])
[ 2879.677377] bttv0: using tuner=5
[ 2879.677390] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[ 2879.677398] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[ 2879.701868] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[ 2879.710471] bttv0: registered device video0
[ 2879.710504] bttv0: registered device vbi0
[ 2879.710531] bttv0: registered device radio0
[ 2879.710557] bttv0: PLL: 28636363 => 35468950 . ok
[ 2879.724188] input: bttv IR (card=72) as /class/input/input9
```

---

