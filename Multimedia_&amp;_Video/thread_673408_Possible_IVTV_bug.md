---
title: "Possible IVTV bug?"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by Uberneen on 2008-01-20
I have a functional media center unit that was running 7.04 and working fine with a PVR150 and MythTV.  A few months ago I upgraded to 7.10 and everything went very well, except for some unusual behavior with the video.
After using MythTV and then quiting back to desktop, if I open a video I get audio but the image is just a jumble of green lines with some orange in the background (there's no movement, it's just a static image).
If I go back into MythTV I get the same thing.

At first I thought it might have had to do with Compiz so I disabled it, but it's still happening.  A restart fixes it, but that basically means I have to reboot every time I use MythTV.

Edit: [http://ubuntuforums.org/showthread.php?p=4128104](http://ubuntuforums.org/showthread.php?p=4128104)  -- This screen is much like what I'm seeing, just different colors, and it also effects every video player and video.

Any ideas?

Kernel: 2.6.22-14-generic
Video: AGP Nvidia GeForce 6600

[   41.909429] ivtv0: Encoder revision: 0x02050032
[   41.909435] ivtv0: Recommended firmware version is 0x02060039.
[   41.978641] tveeprom 1-0050: Hauppauge model 26582, rev E6B2, serial# 9784474
[   41.978648] tveeprom 1-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   41.978652] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   41.978655] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   41.978657] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   41.978660] tveeprom 1-0050: has no radio, has no IR receiver, has no IR transmitter
[   41.978664] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   42.057656] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   42.166785] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   45.376144] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   45.475585] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   45.519909] tuner 1-0061: type set to 50 (TCL 2002N)
[   45.828180] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   45.828539] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   45.828898] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   45.829120] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   45.850577] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   45.850618] ivtv:  ====================  END INIT IVTV ====================

---

### Post by tommyp on 2008-01-22
I believe that it is a bug with the nvidia drivers.  The quick workaround that I have used is to adjust the screen resolution or the refresh rate (under preferences) and the video with show up.  You can adjust back and it should work fine.  Something about changing either of these fixed the bug.

---

### Post by Uberneen on 2008-01-23
Thanks for the info, I'll give that a try.

---

