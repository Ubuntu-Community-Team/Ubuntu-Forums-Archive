---
title: "Hauppauge PVR-150 audio, no video"
date: 2008-01-04
forum: Multimedia Production
---

### Post by Mud.Knee.Havoc on 2008-01-04
I finally got my Hauppauge PVR-150 MCE working (sort of).  I'm trying to set up my VCR to convert old tapes onto DVD.  I can hear the audio, but see no video.  It doesn't matter which channel I switch it to, I get a flickery, snowy picture.

I'm trying to use VLC media player to get the card working.

I did notice an error after running dmesg (see last line): 
```
[   40.057398] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3930087744 bytes)
[   40.271745] ivtv0: Encoder revision: 0x02060039
[   40.332555] tveeprom 1-0050: Hauppauge model 26582, rev E6B2, serial# 10433932
[   40.332567] tveeprom 1-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   40.332572] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   40.332577] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   40.332581] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   40.332585] tveeprom 1-0050: has no radio, has no IR receiver, has no IR transmitter
[   40.332591] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   40.359477] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   40.399277] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   43.644817] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   43.740417] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   43.790330] tuner 1-0061: type set to 50 (TCL 2002N)
[   44.100306] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   44.101274] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   44.102254] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   44.103067] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   44.124914] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   44.124974] ivtv:  ====================  END INIT IVTV  ====================

(other stuff)

[ 5188.117424] ivtv-fb: no cards found<3>ivtv-fb: no cards found

```

lspci gives me: 
01:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

I've found a few threads here where people have had this same problem... but all were empty threads!  I know there's got to be a fix for this. :D

I've got a coaxial cable as well as composite cables attached... I don't care which I use, as long as I get one of them going.

Any help is greatly appreciated!

EDIT: more info, in case it helps.  I'm using the generic nv display driver.
"lsmod | grep ivtv_fb" doesn't return anything... I guess this is my problem.
"sudo modprobe ivtv_fb" returns 
FATAL: Error inserting ivtv_fb (/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver/ivtv-fb.ko): No such device

---

### Post by dixonstalbert on 2008-01-05
hello

have you seen this thread?

[URL="http://ubuntuforums.org/showthread.php?t=608768"]


2nd or third post down says you have to install ivtv-utils


good luck....

---

### Post by Mud.Knee.Havoc on 2008-01-05
Hi, thanks for the tip.  I've already got that installed.  I ended up installing Mythbuntu on a separate partition and everything works perfectly (except for MythTV, but I don't care about it), so at least in the meantime I can get some video conversions done. :D  I'll check out that thread and see what they suggest.

---

