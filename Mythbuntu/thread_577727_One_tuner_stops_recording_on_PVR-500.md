---
title: "One tuner stops recording on PVR-500"
date: 2007-10-16
forum: Mythbuntu
---

### Post by billbillerson on 2007-10-16
I decided to upgrade my mythtv setup. I downloaded Mythbuntu 7.10 Release Candidate. Installed and everything was going fine....

I recorded 4 shows. One on channel 5 at 8:00, one on channel 10 at 8:00, one on channel 5 at 9:00, and one on channel 10 at 9:00.

I started to watch the shows and everything was fine until the Channel 10 show at 9:00. It only recorded the first 15 mins. Now I can't watch Live TV and everytime I try to record 2 shows, the first one records but the second doesn't. It shows up at 0 Bytes. 

If I restart it fixes the problem for awhile. I don't have commflag on, so no other jobs are running. 

please help..

---

### Post by billbillerson on 2007-10-16
here is the dmesg results

```

[   15.400000] ivtv:  ==================== START INIT IVTV ====================
[   15.400000] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   15.404000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   15.404000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   16.456000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3712466856 bytes)
[   16.672000] ivtv0: Encoder revision: 0x02060039
[   16.728000] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   16.756000] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   16.760000] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   16.760000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   16.796000] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   20.132000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   20.492000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   20.492000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.492000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.492000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   20.492000] ivtv0: Registered device radio0 for encoder radio
[   20.516000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   20.516000] ivtv:  ======================  NEXT CARD  ======================
[   20.516000] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   20.516000] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   21.192000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (3662309696 bytes)
[   21.408000] ivtv1: Encoder revision: 0x02060039
[   21.412000] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   21.412000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   21.428000] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   24.716000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   24.780000] ivtv1: Correcting tveeprom data: no radio present on second unit
[   24.780000] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   25.144000] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   25.144000] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   25.144000] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   25.144000] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   25.168000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   25.188000] ivtv:  ====================  END INIT IVTV  ====================
[ 8042.420000] ivtv1: DMA TIMEOUT 00000001 0
[ 8050.308000] ivtv1: DMA TIMEOUT 00000001 0
[ 8057.916000] ivtv1: DMA TIMEOUT 00000001 0
[ 8065.556000] ivtv1: DMA TIMEOUT 00000001 0


```

With the DMA TIMEOUT's continuing on....

I also see this:
```

2007-10-16 14:29:57.821 MPEGRec(/dev/video1) Error: select timeout - ivtv driver has stopped responding

```
In the /var/log/mythtv/mythbackend.log

---

### Post by superm1 on 2007-10-16
Do you have VBI enabled?  If so, please disable it and try again.

---

### Post by billbillerson on 2007-10-16
> **superm1 said:**
> Do you have VBI enabled?  If so, please disable it and try again.

What is VBI and where would I check if it is enabled? 

This is pretty much a default install, no settings where changed so far.

---

### Post by superm1 on 2007-10-16
VBI is used for closed captioning.  It is one of the options listed in mythtv-setup.

---

### Post by billbillerson on 2007-10-16
VBI Fomat is set to None.

---

### Post by billbillerson on 2007-10-17
I restarted last night at 7. I recorded 3 shows, one at 8,9, and 10. They worked. This morning I decided to test it out again and started recording 2 shows at at time.

2 shows at 7:00 am --> worked fine
2 shows at 8:00 am --> worked fine
2 shows at 9:00 am --> worked fine
2 shows at 10:00 am --> one show fine the other only 224 MB
2 shows at 12:00 pm --> one show fine the other 0 B

again I have this in /var/log/mythtv/mythbackend.log:
2007-10-17 12:29:54.509 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding


and this in dmesg:
[64837.016000] ivtv0: DMA TIMEOUT 00000001 0

any help???

---

### Post by billbillerson on 2007-10-22
If I only record one show at a time it works fine. I have settled for doing it this way. It just really bothers me that I bought a 2 turner card but can't use both tuners.

---

### Post by superm1 on 2007-10-22
Well two recommendations here. 

1) Bring this up on the ivtv mailing list.

2) Get hauppauge to send you a new card.  This one can very likely be busted.

---

### Post by pgcudahy on 2007-10-24
I've had similar problems with DMA timeouts on one of my two Hauppauge tuners. [This link]("http://www.mythtv.org/wiki/index.php/IVTV#My_console.2Flog_is_full_of_messages_about_IVTV_DMA_errors_and_some_of_my_recordings_are_truncated.21") on the mythtv wiki says there's a problem with IVTV and [here]("http://www.gossamer-threads.com/lists/ivtv/users/36868") they mention upgrading to IVTV 0.10.6. Is there any way to do this within apt-get (i.e. not compiling your own kernel)?

---

