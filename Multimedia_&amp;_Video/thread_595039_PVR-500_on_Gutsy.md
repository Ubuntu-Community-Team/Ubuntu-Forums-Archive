---
title: "PVR-500 on Gutsy"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by maino82 on 2007-10-28
Until recently I was running Fiesty with a custom compiled kernel and the 0.7 series IVTV drivers, under the recommendation of the ivtvdriver.org guides. I just upgraded to Gutsy after hearing that the IVTV drivers were included in the newest kernel and that the PVR-500 works out of the box. Unfortunately, only one tuner gives me a picture, and the other one is just static. I tried to fix the second tuner and ended up getting static on both tuners now. Below is what's in my dmesg. The good people on the ivtv list serve took a look at it and couldn't find out where the problem might lie. Any help you could offer would be greatly appreciated.

```
maino82@thrawn:~$ dmesg | egrep -i '(ivtv|tveeprom|tuner)'
[   37.079035] ivtv:  ==================== START INIT IVTV ====================
[   37.079040] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   37.079481] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   37.079730] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   37.763797] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3752828888 bytes)
[   37.975835] ivtv0: Encoder revision: 0x02050032
[   37.975839] ivtv0: Recommended firmware version is 0x02060039.
[   38.036661] tveeprom 2-0050: Hauppauge model 23552, rev D492, serial# 7971869
[   38.036667] tveeprom 2-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   38.036670] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   38.036673] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   38.036675] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   38.036678] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   38.036680] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   38.036683] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   38.060025] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   38.060058] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   38.063675] tuner 2-0060: TEA5767 detected.
[   38.063677] tuner 2-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   38.063696] tuner 2-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   38.063922] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   38.109142] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   41.407472] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   41.451790] tuner 2-0061: type set to 57 (Philips FQ1236A MK4)
[   41.766549] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   41.766843] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   41.767148] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   41.767355] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   41.767661] ivtv0: Registered device radio0 for encoder radio
[   41.791129] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   41.791313] ivtv:  ======================  NEXT CARD  ======================
[   41.791318] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   41.791390] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   42.432962] ivtv1: loaded v4l-cx2341x-enc.fw firmware (3753829368 bytes)
[   42.647877] ivtv1: Encoder revision: 0x02050032
[   42.647879] ivtv1: Recommended firmware version is 0x02060039.
[   42.652478] tuner 3-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   42.652493] tda9887 3-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   42.655469] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   42.670742] cx25840 3-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   45.947672] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   46.015286] tveeprom 3-0050: Hauppauge model 23552, rev D492, serial# 7971869
[   46.015292] tveeprom 3-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   46.015295] tveeprom 3-0050: TV standards NTSC(M) (eeprom 0x08)
[   46.015298] tveeprom 3-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   46.015301] tveeprom 3-0050: audio processor is CX25843 (idx 37)
[   46.015303] tveeprom 3-0050: decoder processor is CX25843 (idx 30)
[   46.015305] tveeprom 3-0050: has radio, has no IR receiver, has no IR transmitter
[   46.015309] ivtv1: Correcting tveeprom data: no radio present on second unit
[   46.015311] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   46.082662] tuner 3-0061: type set to 57 (Philips FQ1236A MK4)
[   46.390733] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   46.391023] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   46.391327] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   46.391541] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   46.413926] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   46.417014] ivtv:  ====================  END INIT IVTV  ====================

```

---

### Post by cdeszaq on 2007-11-19
I am having the same problem. Same capture card, and same behavior. If you would like any longs, let me know, but they seem to be similar to what's been posted.

---

