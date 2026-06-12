---
title: "TvTime - SECAM sound issue"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by SyL on 2007-01-06
Hi all,

My tvcard is a hauppauge wintv express.

I've got a issue with the sound. Using TvTime i do not have sound if the television standard is set to SECAM (I'm living in france, here the standard is SECAM) but everything is working properly if this is set to PAL -except that i've just got 2 channel from Italia. 
Using the right setting for france i've got then the image with all the right channel but no sound...

Any clue is welcome :)
Thx

---

### Post by SyL on 2007-01-06
I forgot to precise that I've tried all available audio modes (PAL-BG, PAL-I, PAL-DK)


syl@Oniris:/etc/modprobe.d$ dmesg|grep bt
[17179588.320000] bttv: driver version 0.9.16 loaded
[17179588.320000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179588.320000] bttv: Bt8xx card found (0).
[17179588.320000] bttv0: Bt878 (rev 17) at 0000:01:09.0, irq: 201, latency: 32, mmio: 0xe0000000
[17179588.320000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[17179588.320000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179588.320000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[17179588.324000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17179588.880000] bttv0: using tuner=38
[17179588.880000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179588.884000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179588.884000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179589.428000] bttv0: i2c: checking for TDA9887 @ 0x86... found
[17179589.448000] tda9887 2-0043: chip found @ 0x86 (bt878 #0 [sw])
[17179589.476000] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179589.508000] bttv0: registered device video0
[17179589.508000] bttv0: registered device vbi0
[17179589.508000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179589.612000] bt878: AUDIO driver version 0.0.0 loaded
[17181718.008000] bttv0: OCERR @ 1abea014,bits: HSYNC OFLOW FDSR OCERR*

---

### Post by SyL on 2007-01-10
[http://ubuntuforums.org/showthread.php?t=310958](http://ubuntuforums.org/showthread.php?t=310958)

---

