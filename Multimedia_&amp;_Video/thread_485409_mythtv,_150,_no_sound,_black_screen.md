---
title: "mythtv, 150, no sound, black screen"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by little cazy on 2007-06-26
ivtv is fine, and everything worked ( i did all he troublshooting 4 it)
when i do 'dmesg'
> [   44.084961] ivtv:  ==================== START INIT IVTV ====================
[   44.084965] ivtv:  version 0.10.1 (tagged release) loading
[   44.084967] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   44.084970] ivtv:  In case of problems please include the debug info between
[   44.084972] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   44.084974] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   44.085053] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   44.085314] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   44.085318] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   44.085328] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   44.258786] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   44.258791] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 22 (level, high) -> IRQ 17
[   44.258816] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   44.584089] intel8x0_measure_ac97_clock: measured 58825 usecs
[   44.584093] intel8x0: clocking to 46930
[   44.846196] ivtv0: loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   45.063875] ivtv0: Encoder revision: 0x02060039
[   45.131813] tveeprom 2-0050: Hauppauge model 26552, rev G168, serial# 8882162
[   45.131818] tveeprom 2-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   45.131821] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   45.131826] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   45.131829] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   45.131831] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   45.131835] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   45.166925] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   45.166958] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   45.171420] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   45.213821] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   50.182727] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   50.310438] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   50.378421] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   50.378759] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   50.379098] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   50.379296] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   50.379647] ivtv0: Registered device radio0 for encoder radio
[   50.379669] tuner 2-0061: type set to 47 (LG NTSC (TAPE series))
[   50.779736] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   50.779754] ivtv:  ====================  END INIT IVTV  ====================

mythtv also only works (not in coulding the tv plob.) under the mythtv user
and the recording don't show/hear

---

