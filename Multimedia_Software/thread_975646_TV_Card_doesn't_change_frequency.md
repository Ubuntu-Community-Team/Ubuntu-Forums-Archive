---
title: "TV Card doesn't change frequency"
date: 2008-11-08
forum: Multimedia Software
---

### Post by 3stan on 2008-11-08
Hi,

I have tv-card which works under MDK but not with ubuntu. Why?
System finds it, loads drivers and next can't change frequency. If i set in MDK station to XXX, I have XXX under ubuntu on other chanels. Why? 

ola@domek:~$ dmesg | grep bttv
[ 55.169987] bttv: driver version 0.9.17 loaded
[ 55.169993] bttv: using 4 buffers with 2080k (520 pages) each for capture
[ 55.170054] bttv: Bt8xx card found (0).
[ 55.170085] bttv0: Bt878 (rev 2) at 0000:00:07.0, irq: 21, latency: 64, mmio: 0xfc9ff000
[ 55.170208] bttv0: using: Prolink Pixelview PV-BT878P+ (Rev.4C,8E) [card=70,insmod option]
[ 55.170243] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[ 55.170773] bttv0: tuner type=25
[ 55.170776] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[ 55.171240] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[ 55.171703] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[ 56.195407] bttv0: registered device video0
[ 56.195429] bttv0: registered device vbi0
[ 56.195446] bttv0: registered device radio0
[ 56.195465] bttv0: PLL: 28636363 => 35468950 .. ok
[ 56.224336] input: bttv IR (card=70) as /devices/pci0000:00/0000:00:07.0/input/input7
[ 433.858251] bttv0: PLL can sleep, using XTAL (28636363).
[ 441.235711] bttv0: PLL: 28636363 => 35468950 .. ok

==================

scanning channel list europe-west...
E2 ( 48.25 MHz): ???
[unknown (E2)]
channel = E2

E3 ( 55.25 MHz): ???
[unknown (E3)]
channel = E3

E4 ( 62.25 MHz): ???
[unknown (E4)]
channel = E4

S01 ( 69.25 MHz): ???
[unknown (S01)]
channel = S01

---

