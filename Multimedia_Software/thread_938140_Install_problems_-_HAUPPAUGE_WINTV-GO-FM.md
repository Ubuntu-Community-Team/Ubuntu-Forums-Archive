---
title: "Install problems - HAUPPAUGE WINTV-GO-FM"
date: 2008-10-04
forum: Multimedia Software
---

### Post by jmichelsen on 2008-10-04
(Xubuntu Hardy 8.4)
I have been trying to get a proper mythtv or MCE box going for about a month now. I had long ago purchased a crappy external tuner (KWORLD) and I was never able to get that working so I searched around and found a Hauppauge card on ebay that seemed to have some support and promise. Hauppauge website had an install guide for Linux so in haste I figured if that old guide worked back in the day, it should have even better support today and I bought it..well I was wrong. It isnt working. I am new to PC-TV so I was starting pretty much at square one.

I installed the new card, lspci showed it was there, lsmod showed it had loaded the bttv module. 
/dev/video0 was present although "cat /dev/video0 > test.mpg" gave me input/output error.

dmesg showed:

```

jmichelsen@michelsendt:~$ dmesg | grep bttv
[   23.044773] bttv: driver version 0.9.17 loaded
[   23.044777] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   23.044837] bttv: Bt8xx card found (0).
[   23.044851] bttv 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   23.044861] bttv0: Bt878 (rev 2) at 0000:01:06.0, irq: 18, latency: 16, mmio: 0xfdfff000
[   23.044873] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   23.044876] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   23.044907] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init]
[   23.047391] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   23.074545] bttv0: Hauppauge eeprom indicates model#62471
[   23.074548] bttv0: tuner type=2
[   23.074552] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   23.075141] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   23.075650] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   23.168324] bttv0: registered device video0
[   23.168357] bttv0: registered device vbi0
[   23.168389] bttv0: registered device radio0
[   23.169081] bttv0: PLL: 28636363 => 35468950 .. ok
[  740.556916] bttv0: PLL can sleep, using XTAL (28636363).
[  760.220026] bttv0: timeout: drop=26 irq=1648/1648, risc=3064301c, bits: HSYNC OFLOW

```

I thought that was a great sign, it seems to have loaded everything! .. I was wrong, after trying 10 diff tv apps, none of them were able to find the capture card.

Is there something I am missing? I searched all over and cant find any other info that helps.

This old snipit from the mailing list [https://lists.ubuntu.com/archives/ubuntu-users/2005-May/037236.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-May/037236.html) shows what appears to be the same card, working but I tried what he did to no avail.

I could really use some help here.
Any thoughts are appreciated.

---

### Post by jmichelsen on 2008-10-06
*bump* 
Anyone have any ideas? This is a pretty old card and there are variations of it that work, I mean the chipset is supported on other cards (bt878  ) I am just a novice Linux TV user so I need some help troubleshooting this. Any pointers on things I could check or places to look are helpful. Google is still coming up dry.

---

