---
title: "Mplayer stutters; totem works"
date: 2008-05-09
forum: Multimedia Software
---

### Post by rpglover64 on 2008-05-09
I like mplayer.  I don't particularly like Totem.  However, mplayer stutters when playing certain avi files.  It plays fine for periods of time ranging from a few seconds to a few minutes, and then both the video and the audio pause for about a second; the video continues, and the audio makes an abnormally loud noise, as though the sound it missed playing is trying to catch up.  This is coupled with synchronization problems.  I've tried -autosync 30 all the way up to -autosync 200, but it doesn't solve the problem.  I don't know what values of -autosync should be, so I stopped there.  Totem plays these (well, I only tested with one; I'll look at others later) without any problem.

The file info as per MediaInfo:

Format                       : AVI
Format/Info                  : Audio Video Interleave
Format/Family                : RIFF
File size                    : 350 MiB
PlayTime                     : 51mn 35s
Bit rate                     : 949 Kbps
StreamSize/String            : 4.71 MiB
Writing application          : VirtualDub

Video #0
Codec                        : XviD
Codec/Family                 : MPEG-4V
Codec/Info                   : XviD project
Codec profile                : Simple Profile/Level 3
Codec settings, Packet bitst : Yes
Codec settings, BVOP         : Yes
Codec settings, QPel         : No
Codec settings, GMC          : 0
Codec settings, Matrix       : Default
PlayTime                     : 51mn 35s
Bit rate                     : 813 Kbps
Width                        : 624 pixels
Height                       : 352 pixels
Display Aspect ratio         : 16/9
Frame rate                   : 23.976 fps
Resolution                   : 8 bits
Chroma                       : 4:2:0
Interlacement                : Progressive
Bits/(Pixel*Frame)           : 0.154
StreamSize/String            : 300 MiB
Writing library              : XviD 1.1.0Beta1
Writing library/Date         : UTC 2005-01-16

Audio #0
Codec                        : MPEG-1 Audio layer 3
Codec profile                : Joint stereo
PlayTime                     : 51mn 35s
Bit rate mode                : VBR
Bit rate                     : 124 Kbps
Minimum bit rate             : 128 Kbps
Channel(s)                   : 2 channels
Sampling rate                : 48.0 KHz
Resolution                   : 16 bits
StreamSize/String            : 45.6 MiB
Writing library              : LAME3.98a
Encoding settings            : ABR


I think that the VBR audio may be significant.

My system info: I'm running Gutsy on a Dell 1420 (1420n?).

---

### Post by seventyeights on 2008-05-10
I played with a pinnacle mp4 encoder, and I remember seeing symptoms like yours right after I cut out the commercials.  I think mplayer is tripping on choppy data.  I would either get mplayer to rebuild the index, or simply re-encode (just the audio) with ffmpeg or mencoder.

gmplayer -forceidx movie.mpg

---

### Post by rpglover64 on 2008-05-10
-forceidx doesn't fix it.  How would one go about re-encoding just the audio?

---

