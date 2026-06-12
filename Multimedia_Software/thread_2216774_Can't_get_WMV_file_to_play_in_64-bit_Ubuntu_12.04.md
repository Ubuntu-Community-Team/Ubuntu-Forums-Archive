---
title: "Can't get WMV file to play in 64-bit Ubuntu 12.04"
date: 2014-04-13
forum: Multimedia Software
---

### Post by V_Naik on 2014-04-13
I have installed Ubuntu 12.04 LTS on my Dell Inspiron 530. I have some wmv video files from my Windows machine. If I try to open these files usiing any player e.g.
1) VLC Player
2) UM Player
3) SM Player
4) MPlayer Media Player
, it gives only voice. The video comes garbled. 

I have tried:
1) Downloaded and applied restricted update
2) Downloaded and applied videolan codecs. It seems medibuntu website is closed.

I must have spent almost 60 hours trying to fix this. I have also tried to do same thing in Ubuntu 13.10 no luck. Please help if possible.

---

### Post by andrew.46 on 2014-04-14
Can you give a download link for one of the troublesome videos?

---

### Post by mc4man on 2014-04-14
You could also ck. the mplayer log in smplayer or run mplayer from a terminal 
(or identify the vid with mediainfo 

If it's a mms2 then you'll not be able to play on 12.04 64 bit with stock 12.04  media players, if not mms2 then the logs or terminal output could prove informative.

---

### Post by SeijiSensei on 2014-04-14
There was a [problem]("http://ubuntuforums.org/showthread.php?t=1705713") with Windows Media files on 64-bit versions of mplayer because the codecs for WM files are 32-bit.  I don't know whether that is still true; Andrew might have a better understanding of the problem.  All the files I watch use H.264 in the Matroska container.

---

### Post by V_Naik on 2014-04-14
Can you give me more details about [COLOR=#000000]Matroska container?[/COLOR]

---

### Post by V_Naik on 2014-04-14
Format                                   : VC-1
Format profile                           : AP@L1
Codec ID                                 : WVC1
Codec ID/Hint                            : Microsoft
Description of the codec                 : Windows Media Video 9 Advanced Profile
 
Downloaded Matroska, does not seem to support WMV....

---

### Post by andrew.46 on 2014-04-15
> **V_Naik said:**
> Format                                   : VC-1
Format profile                           : AP@L1
Codec ID                                 : WVC1
Codec ID/Hint                            : Microsoft
Description of the codec                 : Windows Media Video 9 Advanced Profile

I would have thought that a modern enough MPlayer could cope with that using ffvc1:

```

andrew@skamandros~$ mplayer Test_1440x576_WVC1_6Mbps.wmv 
MPlayer SVN-r37150-4.8.2 (C) 2000-2014 MPlayer Team

Playing Test_1440x576_WVC1_6Mbps.wmv.
libavformat version 55.37.100 (internal)
ASF file format detected.
[asfheader] Video stream found, -vid 1
**[COLOR="#FF0000"]VIDEO:  [WVC1]  1440x576  24bpp  1000.000 fps  6000.0 kbps (732.4 kbyte/s)[/COLOR]**
Load subtitles in ./
==========================================================================
Requested video codec family [wmvvc1dmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 55.58.103 (internal)
**[COLOR="#FF0000"]Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)[/COLOR]**
==========================================================================
Audio: no sound
Starting playback...
Movie-Aspect is 2.50:1 - prescaling to correct movie aspect.
VO: [xv] 1440x576 => 1440x576 Planar YV12 
V:   5.1   3/  3 ??% ??% ??,?% 0 0 
[VD_FFMPEG] DRI failure.
V:  24.8 497/497 28%  2%  0.0% 0 0 

Exiting... (Quit)

```

You cannot give a link to your file or upload it somewhere? This would take a lot of the guesswork out...
 
> **V_Naik said:**
> Downloaded Matroska, does not seem to support WMV....

'Matroska' refers to a media container rather than a codec or a player so it will be of no help to you in this case :). Matroska btw is the most brilliantly flexible container available today and there are some great tools available for working with it.

---

### Post by V_Naik on 2014-04-16
This is more detail about clip...

MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team

Playing 2003_Sept_TDK 2010_08_31_22_53_21.wmv.
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVC1]  720x480  24bpp  1000.000 fps  4000.0 kbps (488.3 kbyte/s)
Clip info:
 title: 2003_Sept_TDK
Load subtitles in ./
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16002->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Planar YV12
[vc1 @ 0x7facdab483c0]concealing 0 DC, 0 AC, 0 MV errors
[vc1 @ 0x7facdab483c0]concealing 0 DC, 0 AC, 0 MV errors
A:   5.1 V:   5.0 A-V:  0.050 ct:  0.000   2/  2 ??% ??% ??,?% 1 0 ^[[J^M
[vc1 @ 0x7facdab483c0]concealing 0 DC, 0 AC, 0 MV errors

---

### Post by andrew.46 on 2014-04-16
Looks like you have the correct codecs in place to play the file, perhaps a less aged version of MPlayer might get things going? Again, nice to see the file itself....

---

### Post by V_Naik on 2014-04-16
How can I download latest version of mPlayer?

---

### Post by andrew.46 on 2014-04-16
> **V_Naik said:**
> How can I download latest version of mPlayer?

I believe that mc4man runs a PPA with the latest svn MPlayer, have a look here:

[https://launchpad.net/~mc3man/+archive/mplayer-test](https://launchpad.net/~mc3man/+archive/mplayer-test)

I have not tried this PPA, not being a PPA sort of guy, but I would most definitely trust mc4man's work... With this installed it would be interesting to see if your problems are resolved, the current svn is actually 37152:


```

andrew@skamandros~$ svn info svn://svn.mplayerhq.hu/mplayer/trunk
Path: trunk
URL: svn://svn.mplayerhq.hu/mplayer/trunk
Repository Root: svn://svn.mplayerhq.hu/mplayer
Repository UUID: b3059339-0415-0410-9bf9-f77b7e298cf2
Revision: 37152
Node Kind: directory
Last Changed Author: iive
**[COLOR="#FF0000"]Last Changed Rev: 37152[/COLOR]**
Last Changed Date: 2014-04-15 23:12:18 +1000 (Tue, 15 Apr 2014)

```

which represents not only a large number of MPlayer source changes from your own version but also many, many changes to the libavcodec source that MPlayer uses.

---

