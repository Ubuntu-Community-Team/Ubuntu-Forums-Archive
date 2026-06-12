---
title: "Bad recording quality"
date: 2008-03-28
forum: Mythbuntu
---

### Post by JAKEOTR on 2008-03-28
Hi, Im using 0.21 and have been looking over the forums for some answers to why I have some strange recording artifacts, but its hard to describe what kind of problem im having. Its like things are shifting, especially faces during movement. I dont think its an interlacing problem because Ive viewed it both ways. The only thing I can think of is: i'm using svideo from my Dish box to my pvr-150 and somehow the pvr-150 is trying to smooth out all the artifacts inherit in the crappy Dish mega-compressed signal. I'm posting a short segment to illustrate the problem. If anyone knows what I can do to stop or reduce this issue, please let me know, Thanks

 [http://www.sonofotrlives.com/seintest1.mpg](http://www.sonofotrlives.com/seintest1.mpg)

The problem was indeed the temporal filter setting I got off the link below

v4l2-ctl --set-ctrl temporal_filter=0


Strange thing is both of my cards were set to 1 by default

---

### Post by foxbuntu on 2008-03-28
Please post the results for the following here:
```
dmesg | grep ivtv
```

---

### Post by JAKEOTR on 2008-03-29
Sorry about getting back to you so late, but heres the log:

[   25.197679] ivtv:  ==================== START INIT IVTV ====================
[   25.197683] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload ) loading
[   25.197804] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   25.901354] ivtv0: loaded v4l-cx2341x-enc.fw firmware (-139637009756752 bytes)
[   26.278313] ivtv0: Encoder revision: 0x02050032
[   26.278317] ivtv0: Recommended firmware version is 0x02060039.
[   26.330337] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   26.330338] ivtv0: reopen i2c bus for IR-blaster support
[   26.401531] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   26.619367] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   30.068344] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   30.428939] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   30.429224] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   30.429504] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   30.429689] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   30.450579] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   30.450700] ivtv:  ======================  NEXT CARD  ======================
[   30.450704] ivtv1: Autodetected Hauppauge card (cx23415 based)
[   31.086715] ivtv1: loaded v4l-cx2341x-enc.fw firmware (-139637001076768 bytes)
[   31.113841] ivtv1: loaded v4l-cx2341x-dec.fw firmware (-139637001076784 bytes)
[   31.337491] ivtv1: Encoder revision: 0x02050032
[   31.337494] ivtv1: Recommended firmware version is 0x02060039.
[   31.345492] ivtv1: Decoder revision: 0x02020023
[   31.351006] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   31.416503] ivtv1: Autodetected Hauppauge WinTV PVR-250
[   31.498635] saa7115 3-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #1)
[   31.646321] msp3400 3-0040: MSP3445G-B8 found @ 0x80 (ivtv i2c driver #1)
[   31.935420] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   31.935703] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   31.935985] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   31.936193] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   31.936507] ivtv1: Registered device radio1 for encoder radio
[   32.004376] ivtv1: Initialized Hauppauge WinTV PVR-250, card #1
[   32.004397] ivtv:  ====================  END INIT IVTV  ====================


Thanks

---

### Post by JAKEOTR on 2008-03-30
bump

---

### Post by novellahub on 2008-04-01
See here:

[http://www.knoppmythwiki.org/index.php?page=PictureQualityIssues](http://www.knoppmythwiki.org/index.php?page=PictureQualityIssues)

Try changing your capture profile settings explained in this section of the link:

> Try fiddling with the capture resolution in your recording profile. The 480x480 default may be related to issues with certain drivers/firmware. For NTSC try changing it to 720x480 or even 640x480 and boost the bit rates appropriately. BTW - You're not doing this to improve the picture by increasing the resolution, but rather to change the encoding and memory access patterns. It's a strange voodoo hack, but easy enough to try if nothing else works. The IVTV folks say that this is related to some issues with temporal filtering.

---

### Post by JAKEOTR on 2008-04-01
I have set the recording settings to 720x480...and tried the bitrates from low end to high to no avail. Recording HD channels (downrezzed from the Dish) looks much better, but you can still see those "liquid" artifacts, especially in faces. I can try the temporal filter tonight and see if it changes anything. I'm still not sure if the svideo connection would cause the problem, but its either that or the coax input, and thats terrible. Anyone else with Dish have this problem? Dish's quality has really tanked over the last 5 years or so....I'm thinking of trying cable again just to get some quality back.

---

### Post by JAKEOTR on 2008-04-01
I was thinking of trying some recording filters (denoise3d) etc., but I cant seem to enter them under 0.21. Anyone know how to do this? The area is greyed out in the settings.

---

