---
title: "All of a sudden, vlc says no to dvds"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2007-03-26
Hi there,

I was wondering if anyone could help me.  I've had vlc running ever since installing ubuntu and been playing divx, xvid, dvds, etc.  But I opened it up today and it won't play any dvds.  It either crashes or just sits there.  And if it just sits there what usually happens is I see an extra set of controls pop up (it looks like the play/pause and nav controls) for about a half a second and then does nothing.  At the same time it still plays all the divx and other compressed video files on the local disk.

I reinstalled vlc and still no luck.

What could I do to fix this?

Thanks for the help,
Douglas

---

### Post by simonn on 2007-03-26
Try running vlc from a terminal and posting any error (or other) messages when you try playing a DVD.

---

### Post by djrobthaman on 2007-03-28
Simonn,

Sorry for the length, but here is the output in the terminal

Douglas

```

VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: Casino Royale
libdvdnav: DVD Serial Number: 36314ee1
libdvdnav: DVD Title (Alternative): Casino Royale
libdvdnav: Unable to find map file '/home/douglas/.dvdnav/Casino Royale.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x05
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x06
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x05
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x06
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x05
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x06
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
[00000286] main playlist: nothing to play

```

---

### Post by simonn on 2007-03-28
"libdvdread: Encrypted DVD support unavailable."

Did this dvd ever work?

I suspect that you need to install libdvdcss (DISCLAIMER: this may be illegal where you are located):

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28restricted%29)

---

### Post by djrobthaman on 2007-03-29
Hi,

Yes, vlc used to work with dvds before.  Now it chokes up whenever I load any dvd.  I went ahead and installed libdvdcss2 (apparently it wasn't installed) but it still has a problem.  Now it crashes every time I try to open a dvd.  

Also installed regionset but that didn't help either.  Do you think there's anything else I can do?

Thanks

---

### Post by simonn on 2007-03-29
How about running it from the command line and posting the output again? After all you have made some changes, so maybe you are getting different errors now?

Or, do you think the description you have given is enough to go on?

---

### Post by djrobthaman on 2007-03-29
Ok, here it is.  It turns out in trying to open one dvd there was so much output that I couldn't scroll to the beginning where I had opened vlc, but here is what I could copy.

```

libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_51_1.VOB at 0x003eb305
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_52_0.VOB at 0x003eb47f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_52_1.VOB at 0x003eb583
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_53_0.VOB at 0x003eb6fd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_53_1.VOB at 0x003eb801
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_54_0.VOB at 0x003eb97b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_54_1.VOB at 0x003eba7f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_55_0.VOB at 0x003ebbf9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_55_1.VOB at 0x003ebcfd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_56_0.VOB at 0x003ebe77
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_56_1.VOB at 0x003ebf7b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_57_0.VOB at 0x003ec0f5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_57_1.VOB at 0x003ec1f9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_58_0.VOB at 0x003ec373
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_58_1.VOB at 0x003ec477
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_59_0.VOB at 0x003ec5f1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_59_1.VOB at 0x003ec6f5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_60_0.VOB at 0x003ec86f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_60_1.VOB at 0x003ec973
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_61_0.VOB at 0x003ecaed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_61_1.VOB at 0x003ecbf1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_62_0.VOB at 0x003ecd6b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_62_1.VOB at 0x003ece6f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_63_0.VOB at 0x003ecfe9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_63_1.VOB at 0x003ed0ed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_64_0.VOB at 0x003ed267
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_64_1.VOB at 0x003ed36b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_65_0.VOB at 0x003ed4e5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_65_1.VOB at 0x003ed5e9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_66_0.VOB at 0x003ed763
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_66_1.VOB at 0x003ed867
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_67_0.VOB at 0x003ed9e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_67_1.VOB at 0x003edae5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_68_0.VOB at 0x003edc5f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_68_1.VOB at 0x003edd63
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_69_0.VOB at 0x003ededd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_69_1.VOB at 0x003edfe1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_70_0.VOB at 0x003ee15b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_70_1.VOB at 0x003ee25f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_71_0.VOB at 0x003ee3d9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_71_1.VOB at 0x003ee4dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_72_0.VOB at 0x003ee657
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_72_1.VOB at 0x003ee75b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_73_0.VOB at 0x003ee8d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_73_1.VOB at 0x003ee9d9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_74_0.VOB at 0x003eeb53
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_74_1.VOB at 0x003eec57
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_75_0.VOB at 0x003eedd1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_75_1.VOB at 0x003eeed5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_76_0.VOB at 0x003ef04f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_76_1.VOB at 0x003ef153
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_77_0.VOB at 0x003ef2cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_77_1.VOB at 0x003ef3d1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_78_0.VOB at 0x003ef54b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_78_1.VOB at 0x003ef64f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_79_0.VOB at 0x003ef7c9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_79_1.VOB at 0x003ef8cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_80_0.VOB at 0x003efa47
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_80_1.VOB at 0x003efb4b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_81_0.VOB at 0x003efcc5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_81_1.VOB at 0x003efdc9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_82_0.VOB at 0x003eff43
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_82_1.VOB at 0x003f0047
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_83_0.VOB at 0x003f01c1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_83_1.VOB at 0x003f02c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_84_0.VOB at 0x003f043f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_84_1.VOB at 0x003f0543
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_85_0.VOB at 0x003f06bd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_85_1.VOB at 0x003f07c1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_86_0.VOB at 0x003f093b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_86_1.VOB at 0x003f0a3f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_87_0.VOB at 0x003f0bb9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_87_1.VOB at 0x003f0cbd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_88_0.VOB at 0x003f0e37
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_88_1.VOB at 0x003f0f3b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_89_0.VOB at 0x003f10b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_89_1.VOB at 0x003f11b9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_90_0.VOB at 0x003f1333
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_90_1.VOB at 0x003f1437
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_91_0.VOB at 0x003f15b1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_91_1.VOB at 0x003f16b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_92_0.VOB at 0x003f182f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_92_1.VOB at 0x003f1933
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_93_0.VOB at 0x003f1aad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_93_1.VOB at 0x003f1bb1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_94_0.VOB at 0x003f1d2b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_94_1.VOB at 0x003f1e2f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_95_0.VOB at 0x003f1fa9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_95_1.VOB at 0x003f20ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_96_0.VOB at 0x003f2227
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_96_1.VOB at 0x003f232b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_97_0.VOB at 0x003f24a5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_97_1.VOB at 0x003f25a9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_98_0.VOB at 0x003f2723
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_98_1.VOB at 0x003f2827
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_99_0.VOB at 0x003f29a1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_99_1.VOB at 0x003f2aa5
libdvdread: Elapsed time 0
libdvdread: Found 99 VTS's
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x05
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x06
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x05
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x06
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x05
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x06
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:618
    for cell_position[i].zero_1 = 0x04
Segmentation fault (core dumped)

```

---

### Post by simonn on 2007-03-29
It is obviously not a problem due to css encryption as the DVD now decrypts ok - the libdvdread: Get key for... messages - after installing libdvdcss.

I have googled on the Zero check failed in ifo_read.c:618 to no avail, well there were search results, but no answers.

Things do not "just happen" with computers. Did you upgrade ANY packages inbetween the last time you played a dvd and this problem occuring? Have you tried anyother media players - mplayer , totem?

---

### Post by djrobthaman on 2007-03-29
Yeah man,

I know things just don't happen like that.  I just don't know how to pinpoint the problem.  I've performed countless upgrades since installing and last using vlc.  I'm actually nont 100% sure when the last time I used it for a dvd was.  I have installed beryl/xgl, mythtv (not that it works, i guess i should uninstall... stupid ati video card), amarok, gdesklets, nfts-3g drivers and nspluginwrapper (so i can use flash).  I believe so far those have been my only major installs.  I guess you could also count mysql server 5 because that's a pre-req for myth.

I don't know if this may be an indicator of anything to do with dvd playback, but ubuntu is reading one of my fat32 drives (i know it's fat32 cuz i formatted it that way in ubuntu) as ntfs and the only way i can read/write to it is to mount it as such.  I don't think that has any relation though.  Do you?

Thanks for all your help,
Douglas

---

### Post by stkaplan on 2007-04-03
Is Casino Royale the only DVD you've tried? There seem to be a lot of issues with a new type of copy protection, which Casino Royale uses. Try a different disc.

Windows has the same problem as well (or at least, a similar one). So it might not be an issue with your installation.

---

### Post by djrobthaman on 2007-04-04
Hmmm... Interesting.  I'll try and see if it works on any old dvds.  I think I tried 2 others as well and they didn't work, but more than likely they're new as well  (don't quite remember which ones).

If this is the problem, that there's a new encryption out there, do you know if there is a package I can install that would allow me to decrypt?

Thanks

---

### Post by djrobthaman on 2007-04-05
Hi,

Tried using old dvd's and it still didn't work.  But, based on some looking around, downloaded kaffeine and that plays dvds fine.  I know I could just use kaffeine for dvd's and vlc for everything else, but I like to have everything all in one place.  And I love vlc.

So, is there any way for me to make vlc piggy back off of whatever library/package/whatever kaffeine is using to play dvd's?  (BTW, tried vlc after installing kaffiene and it still crashes)

Thanks

---

### Post by airtonix on 2007-04-14
just a thought : 

first install apt-on-cd(its in the repos)

> sudo apt-get install aptoncd

then uninstall all the movie player you have installed...

> sudo apt-get remove blah blah

then do a 
> sudo apt-get clean && sudo apt-get autoremove && sudo apt-get update && sudo apt-get upgrade 

and  
then install vlc libdvdcss2 gstreamer-bad etc etc (source : [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ) 
or use the add remove gui widget as the page suggests

hope that helps as a suggestion?

---

