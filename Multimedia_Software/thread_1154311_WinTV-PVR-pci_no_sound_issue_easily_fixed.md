---
title: "WinTV-PVR-pci no sound issue easily fixed"
date: 2009-05-09
forum: Multimedia Software
---

### Post by kc4zyp on 2009-05-09
WinTV-PVR-pci no sound issue solved.masq-man from Feb 2007 gave the last clues. Thanks :P

First, for the WinTV-PVR-pci TV tuner and FM tuner cards with no apparent sound but a picture, you'll wouldn't need to change a ton of settings. Take the pvrpcidrv15_20045.exe and extract the hcwamc.rbf driver file from it. You can do this this by installing it (self extracting on install) under a MS Windows OS plateform (98SE-to-XP)  if you already haven't, or just copying the file if you already have the MS WinTV- PVR-pci installed. Linux seems to like to be case picky, so make sure hcwamc.rbf is saved or renamed to all lower case letters or you'll never get sound.

Secondly, at least under Ubuntu, copy hcwamc.rbf driver (all lower case spelling) to the /lib/firmware folder. It may really need to be under the /lib/firmware/2.6-your kernal version-generic folder. To be sure I also have the file saved in each kernal folder besides the /lib/firmware folder.

You don't need to load or unload stuff for sound now and waste a lot of time like I did if you have hcwamc.rbf driver available in the first place. Here is the link for pvrpcidrv15_20045.exe :  [http://www.hauppauge.com/Pages/support/support_pvrpci.html#drv](http://www.hauppauge.com/Pages/support/support_pvrpci.html#drv) 
 or look under the Hauppauge.com web site: Support-> Legacy Products-> WinTV-PVR-PCI. 
[http://www.hauppauge.com/site/support/support.html](http://www.hauppauge.com/site/support/support.html)
Perhaps the driver for other WinTV card types with the no sound issue could be done the same way with their MS install drivers. Hal :P

Notice below that the sound functions under msp3400 and bt878 now finally work:

[   46.462150] Linux video capture interface: v2.00
[   46.708961] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   46.862563] bttv: driver version 0.9.17 loaded
[   46.862567] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   46.862620] bttv: Bt8xx card found (0).
[   46.862640] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 19 (level, low) -> IRQ 17
[   46.862651] bttv0: Bt878 (rev 17) at 0000:01:02.0, irq: 17, latency: 64, mmio: 0xfdfff000
[   46.862755] bttv0: detected: Hauppauge WinTV/PVR [card=80], PCI subsystem ID is 0070:4500
[   46.862758] bttv0: using: Hauppauge WinTV PVR [card=80,autodetected]
[   46.862785] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   46.995354] parport_pc 00:06: reported by Plug and Play ACPI
[   46.995433] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   49.075308] bttv0: altera firmware upload ok
[   49.075912]  sdb1 sdb2 sdb3 sdb4 < sdb5 sdb6 sdb7 >
[   49.107042] sd 4:0:0:0: [sdb] Attached SCSI disk
[   49.107079] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   49.193744] tveeprom 0-0050: Hauppauge model 45231, rev D323, serial# 4257612
[   49.193747] tveeprom 0-0050: tuner model is Philips FM1236 (idx 23, type 2)
[   49.193750] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x0
[   49.193752] tveeprom 0-0050: audio processor is MSP3435 (idx 10)
[   49.193753] tveeprom 0-0050: has radio
[   49.193755] bttv0: Hauppauge eeprom indicates model#45231
[   49.193757] bttv0: tuner type=2
[   49.194035] bttv0: i2c: checking for MSP34xx @ 0x80... found
[   49.221533] msp3400 0-0040: MSP3435G-B6 found @ 0x80 (bt878 #0 [sw]:P
[   49.221536] msp3400 0-0040: MSP3435G-B6 supports radio, mode is autodetect and autoselect:P
[   49.223801] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   49.224413] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   49.294668] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   49.294693] tuner-simple 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   49.294696] tuner 0-0061: type set to Philips NTSC (FI123
[   49.294699] tuner-simple 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   49.294701] tuner 0-0061: type set to Philips NTSC (FI123
[   49.303558] bttv0: registered device video0
[   49.303575] bttv0: registered device vbi0
[   49.303592] bttv0: registered device radio0
[   49.312862] bttv0: PLL: 28636363 => 35468950 .. ok
[   49.405402] bt878: AUDIO driver version 0.0.0 loaded:P
[   49.405442] bt878: Bt878 AUDIO function found (0).:P
[   49.405463] ACPI: PCI Interrupt 0000:01:02.1[A] -> GSI 19 (level, low) -> IRQ 17
[   49.405470] bt878_probe: card id=[0x45000070], Unknown card.
[   49.405471] Exiting..
[   49.405476] ACPI: PCI interrupt for device 0000:01:02.1 disabled
[   49.405481] bt878: probe of 0000:01:02.1 failed with error -22

---

