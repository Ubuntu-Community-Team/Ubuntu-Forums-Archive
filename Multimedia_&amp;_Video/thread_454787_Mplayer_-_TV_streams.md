---
title: "Mplayer - TV streams"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by gruvsyco on 2007-05-25
So, I have Mplayer (and various front ends) installed and I'm trying to use it to watch TV.

I can open /dev/video0 and it plays fine... for 30 minutes to an hour, then it starts getting jumpy and will eventually start giving me some kind of window that opens and closes repeatedly (I'm assuming an error of some sort).

I have a Hauppauge PVR 150.  I've tried using other apps like VLC and Gxine, Gxine works about the same and I can't figure out how to get VLC to work.

Any ideas on what could be causing the jumpiness or how to fix it?  Attached is my IVTV from my log.

```
ivtv:  ==================== START INIT IVTV ====================
ivtv:  version 0.10.1 (tagged release) loading
ivtv:  Linux version: 2.6.20-15-lowlatency SMP preempt mod_unload 586 
ivtv:  In case of problems please include the debug info between
ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
ivtv:  any module options, when mailing the ivtv-users mailinglist.
ivtv0: Autodetected Hauppauge card (cx23416 based)
ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 22 (level, low) -> IRQ 21
ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
input: PS/2 Logitech Mouse as /class/input/input3
ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
ivtv0: Encoder revision: 0x02050032
ivtv0: Recommended firmware version is 0x02060039.
tveeprom 0-0050: Hauppauge model 26132, rev F1B2, serial# 9692861
tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
tveeprom 0-0050: audio processor is CX25841 (idx 35)
tveeprom 0-0050: decoder processor is CX25841 (idx 28)
tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
ivtv0: Autodetected Hauppauge WinTV PVR-150
ivtv0: reopen i2c bus for IR-blaster support
tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
ivtv0: Registered device video0 for encoder MPEG (4 MB)
ivtv0: Registered device video32 for encoder YUV (2 MB)
ivtv0: Registered device vbi0 for encoder VBI (1 MB)
ivtv0: Registered device video24 for encoder PCM audio (1 MB)
tuner 0-0061: type set to 50 (TCL 2002N)
ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
ivtv:  ====================  END INIT IVTV  ====================
```

---

