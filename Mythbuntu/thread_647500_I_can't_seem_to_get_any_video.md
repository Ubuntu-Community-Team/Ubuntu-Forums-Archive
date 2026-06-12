---
title: "I can't seem to get any video"
date: 2007-12-22
forum: Mythbuntu
---

### Post by twooten on 2007-12-22
Hi all,

I've been using Mythdora 3.2 for several months now but just bought a new 750gb hard drive and thought what a great opportunity to upgrade. Tried to upgrade to Mythdora 4 but ran into problems and so stumbled upon Mythbuntu. I really like the look so I have decided to run Mythbuntu if I can get it all working correctly. 

For whatever reason, I can not get my video to play, all I get is what appears to be scrambled input. It's not a black screen, not static, no squiggly lines. I hope that makes sense.

This is my hardware;

ASUS A8N32-SLI Deluxe mobo
Hauppauge pvr-500 capture card
Nvidia 6600 video card
1.5gb RAM

All this hardware worked fine while I was running MythDora 3.2. I bought a new hard drive but since I've been having problems, I put all the original hardware back together because I know it works.

If I pull my video in from my capture card and plug it directly into my tv, i get cable just as I should, so i know the set top box is providing a good signal.

I've been pulling my hair out for 2 days now but I'm still no farther along. I did a normal Mythbuntu install, nothing fancy, nothing unusual. Perhaps it's ivtv drivers? Tried using tvtime but still same problem so my hunch is it's a driver issue.

Any help right now would be great. Mythbuntu looks fantastic! Great job on the interface and install scripts, etc.

I guess I should also mention that I have my schedule direct account set up and working properly. mythfilldatabase has run and I have data in the database. If I hit the 's' key while in watch tv mode, the schedule listings come up and I can change channels.

Thanks,

Tim

---

### Post by twooten on 2007-12-22
the ivtv module does not seem to be loading. From this page [http://ubuntuforums.org/showthread.php?p=3989685](http://ubuntuforums.org/showthread.php?p=3989685) I found this,

=========================================
To make sure that the ivtv-fb module loads without errors, in a terminal window, do

lsmod | grep ivtv_fb
to see whether the module is loaded. If there is no output from the command, the module is not loaded. In this case, execute

sudo modprobe ivtv_fb
=========================================

lsmod | grep ivtv_fb gives me nothing so I tried sudo modprobe ivtv_fb and got the following error.

twooten@leo:~$ sudo modprobe ivtv_fb
FATAL: Error inserting ivtv_fb (/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver/ivtv-fb.ko): No such device

Any ideas??

Thanks,

Tim

---

### Post by twooten on 2007-12-22
[   40.682047] ivtv:  ==================== START INIT IVTV ====================
[   40.682052] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload ) loading
[   40.682187] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   41.356508] ivtv0: loaded v4l-cx2341x-enc.fw firmware (-139636483516224 bytes)
[   41.571798] ivtv0: Encoder revision: 0x02050032
[   41.571802] ivtv0: Recommended firmware version is 0x02060039.
[   41.628005] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   41.723927] tuner 2-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   41.724218] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   41.816502] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   45.411507] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   45.772353] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   45.772683] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   45.773004] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   45.773221] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   45.773553] ivtv0: Registered device radio0 for encoder radio
[   45.796130] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   45.796269] ivtv:  ======================  NEXT CARD  ======================
[   45.796273] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   46.431035] ivtv1: loaded v4l-cx2341x-enc.fw firmware (-139636501994112 bytes)
[   46.649147] ivtv1: Encoder revision: 0x02050032
[   46.649149] ivtv1: Recommended firmware version is 0x02060039.
[   46.654687] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   46.669724] cx25840 3-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   49.958471] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   50.021800] ivtv1: Correcting tveeprom data: no radio present on second unit
[   50.021803] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   50.394262] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   50.394603] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   50.394959] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   50.395215] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   50.416908] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   50.496761] ivtv:  ====================  END INIT IVTV  ====================
[  848.759711] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[  848.759717] ivtv0: Cause: the application is not reading fast enough.
[  863.654585] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[  863.654590] ivtv0: Cause: the application is not reading fast enough.
[ 3835.811034] ivtv-fb: no cards found<3>ivtv-fb: no cards found<3>ivtv-fb: no cards found<3>ivtv-fb: no cards found<3>ivtv-fb: no cards found<3>ivtv-fb: no cards found<3>ivtv-fb: no cards found

---

### Post by twooten on 2007-12-22
anybody???

---

### Post by twooten on 2007-12-22
to help solve this problem?

Thanks,

Tim

---

### Post by twooten on 2007-12-23
I would really appreciate some hints/tips here.

Thanks

---

### Post by Bealer on 2007-12-24
I've got nVidia problems too. Used to work out of the box in Edgy.

I boot up Gutsy using the "nvidia" driver, but just get a black screen. The "vesa" driver works fine.

I'll post if I find a solution.

---

