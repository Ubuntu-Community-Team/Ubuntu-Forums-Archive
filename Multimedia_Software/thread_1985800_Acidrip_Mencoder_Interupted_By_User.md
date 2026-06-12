---
title: "Acidrip: Mencoder Interupted By User"
date: 2012-05-23
forum: Multimedia Software
---

### Post by mrawesome22 on 2012-05-23
I've been trying for 2 days to fix this on my own. So far this is the first problem I cannot find a fix for by using google. Any thoughts would be greatly appreciated.

> Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
MP3 audio selected.
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: XviD (720x480 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=720x540, sampled=720x480
xvid: bitrate setting is ignored during first pass
xvid: 2Pass Rate Control -- 1st pass
[mpeg2video @ 0x7f0c42866300]ac-tex damaged at 44 6
[mpeg2video @ 0x7f0c42866300]Warning MVs not available
[mpeg2video @ 0x7f0c42866300]concealing 1080 DC, 1080 AC, 1080 MV errors
Pos:   0.0s      1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]

Writing header...
ODML: vprp aspect is 4:3.
Setting audio delay to 0.024s.
Writing header...
ODML: vprp aspect is 4:3.
Setting audio delay to 0.024s.

1 duplicate frame(s)!
Pos:   0.0s      2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.003 [0:0]


Skipping frame!
Pos:   0.7s     22f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.037 [0:32]


Skipping frame!
Pos:   1.0s     32f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.037 [71:32]


Skipping frame!
Pos:   1.3s     42f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.037 [58:32]


Skipping frame!
Pos:   1.6s     52f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.037 [50:32]


Skipping frame!
Pos:   1.9s     62f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.037 [45:32]


Skipping frame!
Pos:  46.5s   1399f ( 2%) 86.94fps Trem:   8min 738mb  A-V:0.037 [3755:232]


Skipping frame!
Pos:  46.8s   1409f ( 3%) 87.27fps Trem:   8min 737mb  A-V:0.037 [3732:231]


Skipping frame!
Pos:  47.1s   1419f ( 3%) 87.62fps Trem:   8min 734mb  A-V:0.037 [3709:230]


Skipping frame!
Pos:  47.4s   1429f ( 3%) 87.99fps Trem:   8min 724mb  A-V:0.036 [3686:229]


1 duplicate frame(s)!
Pos:  48.5s   1464f ( 3%) 87.76fps Trem:   8min 736mb  A-V:-0.039 [3775:229]


1 duplicate frame(s)!
Pos:  49.1s   1479f ( 3%) 87.59fps Trem:   8min 745mb  A-V:-0.037 [3857:229]


Skipping frame!
Pos: 735.2s  22043f (54%) 86.44fps Trem:   3min 802mb  A-V:0.038 [4726:249]


1 duplicate frame(s)!
Pos: 737.3s  22104f (54%) 86.48fps Trem:   3min 801mb  A-V:-0.037 [4723:249]


Skipping frame!
Pos:1318.9s  39534f (95%) 87.73fps Trem:   0min 776mb  A-V:0.037 [4479:250]


Skipping frame!
Pos:1319.2s  39544f (95%) 87.75fps Trem:   0min 776mb  A-V:0.037 [4478:250]


1 duplicate frame(s)!
Pos:1321.0s  39599f (95%) 87.78fps Trem:   0min 776mb  A-V:-0.039 [4475:250]


1 duplicate frame(s)!
Pos:1321.5s  39612f (96%) 87.79fps Trem:   0min 775mb  A-V:-0.037 [4475:250]

File not found: 'Susie'
Failed to open Susie.
Cannot open file/device.

Exiting...
AcidRip message - Clearing 2 remaining playlist items
AcidRip message - Mencoder interrupted by userI had this exact same problem in Mint 13, so I switched back to Ubuntu 12.04 Gnome Shell Remix but the problem persists.

These are DVD's that I own and I'm just trying to back them up. This is Seinfeld Season 8. Season seven went without incident, and so did some of season 8. 

I got to episode 15 of season 8 and started getting this. I've tried xvid, divx, and x264 all with same results.

Only thing I can think of is the copy protection switched or something. :confused:

Thank you for your time.

This forum is awesome. I found lots of solutions here just from googling. Ubuntu is awesome as is Gnome Shell!:)

---

### Post by mrawesome22 on 2012-05-23
Figured it out. It was the naming scheme.

Seinfeld_Season_8_E15_The Susie = no go.
Seinfeld_Season_8_E15_TheSusie = works great.

Does Linux have a no spaces rule or something?

Anyway, maybe this will help someone one day.

---

