---
title: "PVR-150/ivtv loads properly, but cannot be controlled"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by dallingham on 2007-05-03
After upgrading to Feisty, my PVR-150 card has started acting strange. While the device loads properly, I cannot use ivtvctl to control it. This card worked properly under Edgy.

dona@shaun:~$ ivtvctl -p 1
not an ivtv driver device

I can grab static from /dev/video0 (since it is not tuned to anything), so capture appears to be working.

Any ideas as to what the problem is? There are no errors in the log files:

[   46.447747] ivtv:  ==================== START INIT IVTV ====================
[   46.447751] ivtv:  version 0.10.1 (tagged release) loading
[   46.447753] ivtv:  Linux version: 2.6.20-15-386 mod_unload 486 
[   46.447755] ivtv:  In case of problems please include the debug info between
[   46.447757] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   46.447758] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   46.447831] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   47.223173] ivtv0: loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   47.435980] ivtv0: Encoder revision: 0x02060039
[   47.506109] tveeprom 0-0050: Hauppauge model 26582, rev C699, serial# 8450455
[   47.506114] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   47.506117] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   47.506119] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   47.506121] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   47.506124] tveeprom 0-0050: has no radio, has no IR receiver, has no IR transmitter
[   47.506127] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   47.540652] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   47.628024] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   52.672821] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   52.810438] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   52.878895] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   52.879128] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   52.879366] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   52.879512] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   52.879667] tuner 0-0061: type set to 50 (TCL 2002N)
[   53.270619] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   53.270636] ivtv:  ====================  END INIT IVTV  ====================

Thanks, 

Don

---

