---
title: "[SOLVED] tuner doesn't seem to be working"
date: 2008-01-06
forum: Mythbuntu
---

### Post by jleiss on 2008-01-06
Good Afternoon,

Just did my first install of mythbuntu, and things seemed to be smooth except none of the tuner inputs seem to be working.

my card seems to be detected fine.

[   34.038539] ivtv:  ==================== START INIT IVTV ====================
[   34.038543] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   34.038632] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   34.038872] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   34.716155] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3248868352 bytes)
[   34.928017] ivtv0: Encoder revision: 0x02050032
[   34.928021] ivtv0: Recommended firmware version is 0x02060039.
[   34.982064] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   35.003106] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   35.006722] tuner 2-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   35.006955] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   35.030212] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   38.303786] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   38.662043] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   38.662279] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   38.662521] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   38.662693] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   38.662947] ivtv0: Registered device radio0 for encoder radio
[   38.686273] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   38.686329] ivtv:  ======================  NEXT CARD  ======================
[   38.686333] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   38.686586] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   39.317707] ivtv1: loaded v4l-cx2341x-enc.fw firmware (3248869352 bytes)
[   39.531228] ivtv1: Encoder revision: 0x02050032
[   39.531230] ivtv1: Recommended firmware version is 0x02060039.
[   39.535768] tuner 3-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   39.538742] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   39.553956] cx25840 3-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   42.818615] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   42.879599] ivtv1: Correcting tveeprom data: no radio present on second unit
[   42.879601] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   43.237333] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   43.237564] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   43.237810] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   43.238007] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   43.260296] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   43.262445] ivtv:  ====================  END INIT IVTV  ====================

Any ideas of why myth would be havin issues using my card?

---

### Post by superm1 on 2008-01-06
check and make sure that you chose the MPEG hw encoding tuner in mythtvsetup.  Also make sure that you bound the proper input to a video source.

---

### Post by jleiss on 2008-01-06
> **superm1 said:**
> check and make sure that you chose the MPEG hw encoding tuner in mythtvsetup.  Also make sure that you bound the proper input to a video source.

my capture card in mythtv is setup to /dev/video0, and when configuring the capture card in myth I am selecting MPEG-2 encoder card. I'm not sure if this is what your meaning or not, but I am not seeing your choices in mythtv-setup.

---

### Post by newlinux on 2008-01-06
Defining a video source and assigning a video source to input are items 3 and 4 in mythtv-setup. 

When you say it doesn't work, what do you mean? What happens when you try and watch a station on your tuner (check and post back here the output of your frontend and backend logs, which can be found in /var/log/mythtv/).

---

### Post by superm1 on 2008-01-06
Yes that is correct. I was paraphrasing in abscence of having access to my backend.  Make sure that you were properly associating it with a video source and input type.

---

### Post by jleiss on 2008-01-06
> **newlinux said:**
> Defining a video source and assigning a video source to input are items 3 and 4 in mythtv-setup. 

When you say it doesn't work, what do you mean? What happens when you try and watch a station on your tuner (check and post back here the output of your frontend and backend logs, which can be found in /var/log/mythtv/).

figured out the issue with the feed, roomate had connections wrong and didn't know the svideo connected to reciver was passing video, moved it over and we had feed. Now to move on to other things such as increasing volume on ubuntu, remotes, etc.

---

