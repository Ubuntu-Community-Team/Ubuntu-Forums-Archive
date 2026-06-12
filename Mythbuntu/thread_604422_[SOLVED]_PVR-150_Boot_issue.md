---
title: "[SOLVED] PVR-150 Boot issue"
date: 2007-11-06
forum: Mythbuntu
---

### Post by bachmand on 2007-11-06
Hi,

I have just purchased a Hauppauge PVR-150 to add to my MythBuntu 7.10 setup.

When I install the card the PC won't boot in MythBuntu, neither from HD nor from CD (WinXP boots fine).

I have tried in 3 different PC's (both AMD and Intel procs.), but same result: boot's fine in WinXP but won't boot into MythBuntu 7.10.

It always stop in the same place (see attached img).

Regards Jan

**Update:** Card has been returned to shop. Failed to install Hauppauge driver under WinXP.

---

### Post by tgm4883 on 2007-11-06
So you are saying that the card was bad?

---

### Post by bachmand on 2007-11-06
> **tgm4883 said:**
> So you are saying that the card was bad?

Yes, just got the message from the Shop, they replaced the board. I will pick it up tomorrow and then see how it goes.

/bachmand

---

### Post by bachmand on 2007-11-07
It was the PVR-150 that was defctive. Just got a new board today, and everything seems to be working.

ubuntu@ubuntu:~$ dmesg | grep -i ivtv
[   81.925971] ivtv:  ==================== START INIT IVTV ====================
[   81.925975] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   81.926059] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   81.926471] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   82.664156] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3543646056 bytes)
[   82.878134] ivtv0: Encoder revision: 0x02050032
[   82.878137] ivtv0: Recommended firmware version is 0x02060039.
[   82.936950] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   83.055246] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   83.058253] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   83.084426] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   86.363725] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   86.721772] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   86.722044] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   86.722301] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   86.722476] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   86.722762] ivtv0: Registered device radio0 for encoder radio
[   86.748501] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   86.748521] ivtv:  ====================  END INIT IVTV  ====================

---

