---
title: "saa7134 compro videomate gold inputs mixed up"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by AyuReady1989 on 2007-03-12
i own a compro videomate gold and my inputs are mixed up i have tried modprobing it and its no use when i switch my tuner to s-video i get a good picture and when i switch the television input i get good sound but no picture anyone have anything that could help me??? I also own a ATI tv wonder pro but i cant even get it to be recognized!! someone help please

---

### Post by josesanders on 2007-03-12
what is the result when you run the command:

$ dmesg

I suspect, as is often the case with saa7134 cards, that it is not being recognized correctly.  There are many different card numbers, each with different input configurations, and if the number isn't recognized correctly, it could cause problems like what you are having.

---

### Post by AyuReady1989 on 2007-03-31
ok i have 2 cards now i recently got a hauppuage wintv but it sucks for gaming because the mpeg encoder has a delay and u cant play a game with a delay was crashing all over the place sry for the delay but here is my dmesg 

[17179592.624000] Linux video capture interface: v1.00
[17179592.720000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179592.780000] ts: Compaq touchscreen protocol output
[17179592.860000] NET: Registered protocol family 10
[17179592.860000] lo: Disabled Privacy Extensions
[17179592.860000] IPv6 over IPv4 tunneling driver
[17179592.888000] intel8x0_measure_ac97_clock: measured 54750 usecs
[17179592.888000] intel8x0: clocking to 46929
[17179592.888000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[17179592.888000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x2000
[17179592.888000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[17179592.888000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 201
[17179592.888000] saa7133[0]: found at 0000:02:08.0, rev: 16, irq: 201, latency: 32, mmio: 0xe6000000
[17179592.888000] saa7133[0]: subsystem: 185b:c100, board: Compro VideoMate TV [card=19,autodetected]
[17179592.888000] saa7133[0]: board init: gpio is cc003f
[17179593.052000] saa7133[0]: i2c eeprom 00: 5b 18 00 c1 ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.052000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.052000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.052000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.052000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.052000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff 01 01 00 ff 00 07 33 01 cb
[17179593.052000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.052000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.064000] ivtv:  ==================== START INIT IVTV ====================
[17179593.064000] ivtv:  version 0.7.0 (tagged release) loading
[17179593.064000] ivtv:  Linux version: 2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179593.064000] ivtv:  In case of problems please include the debug info between
[17179593.064000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179593.064000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179593.276000] tuner 2-0060: TEA5767 detected.
[17179593.276000] tuner 2-0060: chip found @ 0xc0 (saa7133[0])
[17179593.276000] tuner 2-0060: type set to 62 (Philips TEA5767HN FM Radio)
[17179593.284000] tuner 2-0063: chip found @ 0xc6 (saa7133[0])
[17179593.284000] tuner 2-0063: type set to 17 (Philips NTSC_M (MK2))
[17179593.292000] tuner 2-0068: chip found @ 0xd0 (saa7133[0])
[17179593.556000] nvidia: module license 'NVIDIA' taints kernel.
[17179593.808000] saa7133[0]: registered device video0 [v4l2]
[17179593.808000] saa7133[0]: registered device vbi0
[17179593.808000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179593.816000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179593.816000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 209
[17179593.816000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179593.900000] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179594.068000] tveeprom 3-0050: Hauppauge model 26552, rev F1A3, serial# 9933284
[17179594.068000] tveeprom 3-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[17179594.068000] tveeprom 3-0050: TV standards NTSC(M) (eeprom 0x08)
[17179594.068000] tveeprom 3-0050: audio processor is CX25843 (idx 37)
[17179594.068000] tveeprom 3-0050: decoder processor is CX25843 (idx 30)
[17179594.068000] tveeprom 3-0050: has radio, has no IR remote
[17179594.080000] saa7134 ALSA driver for DMA sound loaded
[17179594.080000] saa7133[0]/alsa: saa7133[0] at 0xe6000000 irq 201 registered as card -1
[17179594.096000] tda9887 3-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179594.120000] cx25840 3-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179597.200000] cx25840 3-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[17179597.288000] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179597.968000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179598.184000] ivtv0: Encoder revision: 0x02060039
[17179598.184000] ivtv0 warning: Encoder Firmware can be buggy, use version 0x02040011, 0x02040024 or 0x02050032.
[17179598.184000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179598.184000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179598.184000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179598.184000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179598.184000] ivtv0: Create encoder radio stream
[17179598.184000] tuner 3-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[17179598.284000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[17179598.284000] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[17179598.284000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 201
[17179598.288000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[17179598.288000] ivtv:  ====================  END INIT IVTV  ====================
[17179598.380000] lp0: using parport0 (interrupt-driven).
[17179598.424000] fuse init (API version 7.6)
[17179598.452000] Adding 522104k swap on /dev/disk/by-uuid/58363da0-7a48-4033-beb4-7ed1793e716d.  Priority:-1 extents:1 across:522104k
[17179598.536000] EXT3 FS on hda2, internal journal
[17179600.416000] NET: Registered protocol family 17
[17179603.448000] eth0: no IPv6 routers present
[17179604.588000] ACPI: Power Button (FF) [PWRF]
[17179604.588000] ACPI: Power Button (CM) [PWRB]
[17179604.676000] ibm_acpi: ec object not found
[17179604.700000] pcc_acpi: loading...
[17179607.552000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179607.552000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179607.552000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179613.004000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179613.004000] apm: overridden by ACPI.
[17179629.220000] Bluetooth: Core ver 2.8
[17179629.220000] NET: Registered protocol family 31
[17179629.220000] Bluetooth: HCI device and connection manager initialized
[17179629.220000] Bluetooth: HCI socket layer initialized
[17179629.480000] Bluetooth: L2CAP ver 2.8
[17179629.480000] Bluetooth: L2CAP socket layer initialized
[17179629.484000] Bluetooth: RFCOMM socket layer initialized
[17179629.484000] Bluetooth: RFCOMM TTY layer initialized
[17179629.484000] Bluetooth: RFCOMM ver 1.7

---

