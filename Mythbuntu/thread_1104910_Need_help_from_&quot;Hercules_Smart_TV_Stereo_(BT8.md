---
title: "Need help from &quot;Hercules Smart TV Stereo (BT878)&quot; users !!"
date: 2009-03-24
forum: Mythbuntu
---

### Post by Sdx1978 on 2009-03-24
Hi all,

Any one using the TV card "Hercules Smart TV Stereo" could give me hints to use with Mythbuntu 8.10 freshly installed ?

So far, I did:
1- add "bttv" in /etc/modules
2- put "options bttv radio=0 card=100 tuner=24" in /etc/modprobe.d/bttv

I read the following webpage (French links)
* [Installation d'une carte tuner TV]("http://www.lea-linux.org/documentations/index.php/Hardware-hard_image-tv")
* [Configurer une carte V4L]("http://mythtv-fr.tuxfamily.org/wiki/mythtv-setup_carte_v4l")

with no success.

Final result is card properly detected
> [   11.199019] bttv: driver version 0.9.17 loaded
[   11.199023] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.482517] bttv: Bt8xx card found (0).
[   11.482965] bttv 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   11.482975] bttv0: Bt878 (rev 17) at 0000:01:08.0, irq: 16, latency: 32, mmio: 0xfdeff000
[   11.483016] bttv0: subsystem: 1540:952a (UNKNOWN)
[   11.483021] bttv0: using: Hercules Smart TV Stereo [card=100,insmod option]
[   11.483065] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   11.483121] bttv0: tuner type=24
[   11.483124] bttv0: i2c: checking for TDA9875 @ 0xb0... found
[   11.490119] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   11.624355] bttv0: registered device video0
[   11.624390] bttv0: registered device vbi0
[   11.627162] bttv0: PLL: 28636363 => 35468950 .. ok

if I don't use bttv
> [   10.970512] bttv: driver version 0.9.17 loaded
[   10.970517] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   10.970750] bttv: Bt8xx card found (0).
[   10.971194] bttv 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   10.971204] bttv0: Bt878 (rev 17) at 0000:01:08.0, irq: 16, latency: 32, mmio: 0xfdeff000
[   10.971236] bttv0: subsystem: 1540:952a (UNKNOWN)
[   10.971241] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   10.971285] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   10.998864] bttv0: tuner type unset
[   10.998867] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   11.013334] bttv0: i2c: checking for TDA9875 @ 0xb0... found
[   11.114664] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   11.115295] bttv0: registered device video0
[   11.115328] bttv0: registered device vbi0

lsmod | grep bttv
> bttv                  214100  0
ir_common              55940  1 bttv
compat_ioctl32         18304  1 bttv
videodev               45184  4 tuner,tvaudio,bttv,compat_ioctl32
i2c_algo_bit           15364  1 bttv
v4l2_common            23296  3 tuner,tvaudio,bttv
videobuf_dma_sg        22660  1 bttv
videobuf_core          29828  2 bttv,videobuf_dma_sg
btcx_risc              13832  1 bttv
tveeprom               23428  1 bttv


Who could help on using BT878 card on Mythbuntu, particularly the Hercules one?

Thx.

---

