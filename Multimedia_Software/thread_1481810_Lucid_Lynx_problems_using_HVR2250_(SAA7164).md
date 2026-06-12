---
title: "Lucid Lynx: problems using HVR2250 (SAA7164)"
date: 2010-05-12
forum: Multimedia Software
---

### Post by droethig on 2010-05-12
I have a HVR 2250 card installed. Fresh complete load of 10.04. 
The card is recognized, but /dev/videoX is not created. Also, the
firmware, dvb-fe-tda10048-1.0.fw, is not loaded.

Here's the dmesg (edited for bevity)

[    8.420289] saa7164 driver loaded
[    8.420342] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.420580] CORE saa7164[0]: subsystem: 0070:88a1, board: Hauppauge WinTV-HVR2250 [card=8,autodetected]
[    8.420586] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd400000
[    8.420592] saa7164 0000:02:00.0: setting latency timer to 64
[    8.420596] IRQ 16/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    8.680267] saa7164_downloadfirmware() no first image
[    8.680403] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[    8.680407] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[    8.696970] saa7164_downloadfirmware() firmware read 3978608 bytes.
[    8.696973] saa7164_downloadfirmware() firmware loaded.
[    8.696974] Firmware file header part 1:
[    8.696976]  .FirmwareSize = 0x0
[    8.696978]  .BSLSize = 0x0
[    8.696979]  .Reserved = 0x3cb57
[    8.696980]  .Version = 0x3
[    8.696982] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[    8.696989] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    8.696990] saa7164_downloadfirmware() BSLSize = 0x0
[    8.696992] saa7164_downloadfirmware() Reserved = 0x0
[    8.696993] saa7164_downloadfirmware() Version = 0x51cc1
[   15.040016] saa7164_downloadimage() Image downloaded, booting...
[   15.144019] saa7164_downloadimage() Image booted successfully.
[   15.144037] starting firmware download(2)
[   17.268036] saa7164_downloadimage() Image downloaded, booting...
[   18.932031] saa7164_downloadimage() Image booted successfully.
[   18.932050] firmware download complete.
[   18.968886] tveeprom 0-0000: Hauppauge model 88021, rev C2F2, serial# 6190861
[   18.968890] tveeprom 0-0000: MAC address is 00-0D-FE-5E-77-0D
[   18.968892] tveeprom 0-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
[   18.968895] tveeprom 0-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   18.968898] tveeprom 0-0000: audio processor is SAA7164 (idx 43)
[   18.968900] tveeprom 0-0000: decoder processor is SAA7164 (idx 40)
[   18.968901] tveeprom 0-0000: has radio
[   18.968903] saa7164[0]: Hauppauge eeprom: model=88021
[   19.335005] tda18271 1-0060: creating new instance
[   19.339641] TDA18271HD/C2 detected @ 1-0060
[   19.589208] DVB: registering new adapter (saa7164)
[   19.589215] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   19.877397] tda18271 2-0060: creating new instance
[   19.881469] TDA18271HD/C2 detected @ 2-0060
[   20.144614] tda18271: performing RF tracking filter calibration
[   22.497881] tda18271: RF tracking filter calibration complete
[   22.498167] DVB: registering new adapter (saa7164)
[   22.498172] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...


The saa7164, dvb-core modules are loaded but I have the feeling that more
modules are required. Or is there a special loading order for the modules?

I tried compiling the saa7164 from the sources, but this yielded the same result.

Why isn't /dev/video getting created?

Why isn't dvb-fe-tda10048-1.0.fw getting loaded?


Thanks
Dave

---

### Post by pluto7777 on 2011-03-02
bumping for an answer

---

