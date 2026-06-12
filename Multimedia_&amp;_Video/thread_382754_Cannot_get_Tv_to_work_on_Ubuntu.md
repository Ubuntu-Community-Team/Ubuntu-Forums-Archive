---
title: "Cannot get Tv to work on Ubuntu"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by Les47630 on 2007-03-12
I have search the internet, and been to several forums and I cannot get my Hauppage WinTv card or my Pro 9700 AIW card to work for TVtime, or any other software. It did work in OpenSuse 10.2 without any problems. It shows it with dmesg command. But in TVtime just has a blue screen and show Logitech Quickcam no video /dev/video0. The radio works fine using Gnome Radio. But no tv. 


[17179593.784000] Linux video capture interface: v1.00
[17179593.900000] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.3 $Date: 2005/04/15 19:32:49 $)
[17179593.900000] quickcam: Kernel:2.6.17-11-generic bus:3 class:FF subclass:FF vendor:046D product:0840
[17179593.908000] quickcam: Sensor HDCS-1000/1100 detected
[17179593.908000] quickcam: Registered device: /dev/video0
[17179593.908000] usbcore: registered new driver quickcam


17179594.452000] bttv0: Bt878 (rev 2) at 0000:03:01.0, irq: 209, latency: 32, mmio: 0xeeafe000
[17179594.452000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[17179594.452000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179594.452000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[17179594.456000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17179594.548000] tveeprom 0-0050: Hauppauge model 61381, rev D123, serial# 1449127
[17179594.548000] tveeprom 0-0050: tuner model is Philips FM1236 (idx 23, type 2)
[17179594.548000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[17179594.548000] tveeprom 0-0050: audio processor is MSP3430 (idx 7)
[17179594.548000] tveeprom 0-0050: has radio
[17179594.548000] bttv0: Hauppauge eeprom indicates model#61381
[17179594.548000] bttv0: using tuner=2
[17179594.548000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[17179594.596000] msp3400 0-0040: MSP3430G-A1 found @ 0x80 (bt878 #0 [sw])
[17179594.596000] msp3400 0-0040: MSP3430G-A1 supports radio, mode is autodetect and autoselect
[17179594.600000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179594.604000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179594.632000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179594.660000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179594.660000] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[17179594.692000] bttv0: registered device video1
[17179594.692000] bttv0: registered device vbi0
[17179594.692000] bttv0: registered device radio0
[17179594.756000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179594.792000] ACPI: PCI Interrupt 0000:03:01.1[A] -> GSI 22 (level, low) -> IRQ 209
[17179594.796000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 19 (level, low) -> IRQ 193
[17179594.824000] bt878: AUDIO driver version 0.0.0 loaded
 I really appreciate any help given, I spend a day trying to get it to work.

---

