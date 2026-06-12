---
title: "Hauppauge WinTV 2000 Install"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by lkraemer on 2007-11-04
To get a WinTV 2000 TV Card Working in Ubuntu 7.10

Site used for reference:
http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000

 lspci
01:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
01:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

 lspci -vn
No information displayed on WINTV 2000 card (or Brooktree Corporation Bt878 Video Capture)

 dmesg
[   16.628000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   16.676000] bttv: driver version 0.9.17 loaded
[   16.676000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   16.676000] bttv: Bt8xx card found (0).
[   16.676000] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 20
[   16.676000] bttv0: Bt878 (rev 2) at 0000:01:09.0, irq: 20, latency: 32, mmio: 0xfeaff000
[   16.676000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   16.676000] bttv0: using: Hauppauge (bt878) [card=10,insmod option]
[   16.676000] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init]
[   16.676000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   16.680000] bt878: Unknown symbol bttv_read_gpio
[   16.680000] bt878: Unknown symbol bttv_write_gpio
[   16.680000] bt878: Unknown symbol bttv_gpio_enable
[   16.700000] tveeprom 2-0050: Hauppauge model 38101, rev B210, serial# 1461998
[   16.700000] tveeprom 2-0050: tuner model is Philips FI1236 MK2 (idx 10, type 2)
[   16.700000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   16.700000] tveeprom 2-0050: audio processor is None (idx 0)
[   16.700000] tveeprom 2-0050: has no radio
[   16.700000] bttv0: Hauppauge eeprom indicates model#38101
[   16.700000] bttv0: using tuner=2
[   16.700000] bttv0: i2c: checking for MSP34xx @ 0x80... <6>input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   16.708000] parport_pc 00:09: reported by Plug and Play ACPI
[   16.708000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.712000] parport0: Printer, HP PHOTOSMART 1115
[   16.736000] not found
[   16.736000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   16.736000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   16.816000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   16.864000] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   16.864000] tuner 2-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   16.864000] tuner 2-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   16.880000] bttv0: registered device video0
[   16.880000] bttv0: registered device vbi0
[   16.880000] bttv0: PLL: 28636363 => 35468950 .. ok
[   16.960000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   16.960000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   16.960000] PCI: Setting latency timer of device 0000:00:04.0 to 64

From Above DMESG Card=10 Tuner=2

Open a terminal window
  sudo rmmod bt878
  sudo rmmod bttv
  sudo rmmod tuner
  sudo modprobe bttv card=10 tuner=2


go to /ect
sudo gedit modprobe.conf
add this line: "options bttv card=10 tuner=2"
save in /ect
should work from the next restart

Used Synaptics to install TVTIME

This got VIDEO and Chopped Audio.  By Rotating through the Selections:
TELEVISION
COMPOSITE 1
S-VIDEO
COMPOSITE 3
back to TELEVISION

The Audio quit chopping and everything worked fine.






REFERENCE:
http://kubuntuforums.net/forums/index.php?topic=7038.0

---

### Post by frimilden on 2008-02-26
Worked great and now I am enjoying my TV, thank you for the detailed tut. :popcorn:

---

