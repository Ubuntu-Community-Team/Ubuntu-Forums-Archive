---
title: "play or convert MPEG-TS files, h264 / he-aac using ffmpeg?"
date: 2010-12-03
forum: Multimedia Software
---

### Post by zcat on 2010-12-03
Going mad trying to figure out how to play or convert files transferred from my ZMT620-PVR set-top box. Under ubuntu 10.04 (or mint-DE 091010)

Samples available at [http://zcat.geek.nz/files/zinwell-pvr.zip](http://zcat.geek.nz/files/zinwell-pvr.zip)
50MB download, three 25-second recordings from different channels, the mpeg-ts files can be found in Record-video and have .hidden_filenames

First up have tried totem, vlc, mplayer. None of them even remotely attempt to play the video.

Format of files is MPEG-TS
Video codec appears to be h264
Audio codec is reportedly HE-AAC according to [http://code.google.com/p/zimview/wiki/RecordedVideo](http://code.google.com/p/zimview/wiki/RecordedVideo)

mediainfo-gui says the video codec is AVC (that might be another name for h264?) and audio is MPEG1 layer 1 or layer 3 (different channels use different codecs)

ffprobe says:
Input #0, mpegts, from 'test3.ts':
  Duration: 00:00:25.85, start: 12008.363478, bitrate: 2312 kb/s
    Stream #0.0[0x107]: Video: h264, yuv420p, 720x576 [PAR 16:11 DAR 20:11], 50.60 fps, 50 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x139]: Data: [0][0][0][0] / 0x0000
Unsupported codec (id=102400) for input stream 1

Progress so far; compiled x264 and ffmpeg from SVN using [http://code.google.com/p/x264-ffmpeg-up-to-date/](http://code.google.com/p/x264-ffmpeg-up-to-date/)
also installed faac, faad, libfaac0 and libfaad2 from ubuntu repos.

ffmpeg converts the video just fine but not the audio. Same as above, Stream #0.1[0x139]: Data: [0][0][0][0] / 0x0000 seems to be the only reference to the missing audio stream.

Also tried ffmpeg -acodec copy (because some of the players might be able to handle the raw he-aac stream if we just copy it as-is) but that didn't work either. Same error, it just doesn't seem to recognise #0.1 as being an audio stream at all therefore won't even copy it unmodified.

What else can I try?

---

### Post by andrew.46 on 2010-12-03
Hi zcat,

MPlayer will play the video stream with the following syntax:
```

mplayer -demuxer lavf -vf scale -xy 800 2010Z1127_1036_0.mpg
```

although there are many h264 errors, but I believe mediainfo demonstrates a damaged audio stream, have a look at the duration of the audio:

```

andrew@skamandros~/Desktop$ mediainfo 2010Z1127_1036_0.mpg 
General
Complete name                    : 2010Z1127_1036_0.mpg
Format                           : MPEG-TS
Format profile                   : No PAT/PMT
File size                        : 16.9 MiB
Duration                         : 24s 420ms
Overall bit rate                 : 5 802 Kbps

Video
ID                               : 556 (0x22C)
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Format settings, GOP             : M=4, N=24
**[COLOR="Red"]Duration                         : 24s 420ms[/COLOR]**
Bit rate                         : 5 483 Kbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16:9
Frame rate                       : 50.000 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.119
Stream size                      : 16.0 MiB (95%)
Color primaries                  : BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
Transfer characteristics         : BT.709-5, BT.1361
Matrix coefficients              : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio
ID                               : 606 (0x25E)
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Mode                             : Dual mono
Emphasis                         : 50/15ms
**[COLOR="Red"]Duration                         : 26ms[/COLOR]**
Bit rate mode                    : Constant
Bit rate                         : 32.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Stream size                      : 104 Bytes (0%)

```

This would account for nothing being able to play the sound?

Andrew

---

### Post by mc4man on 2010-12-03
I've gotta try a newer mediainfo, while it  looks about the same, for a few things, most notably this, it's different (see the audio length the same as video
> Format_Settings_Emphasis         : 50/15ms
Duration                         : 24s 746ms
Bit rate mode                    : Constant

Though when I get mplayer to play the audio it does produce 1 extremely short 'sound'

---

### Post by andrew.46 on 2010-12-04
Hi mc4man,

Seems a little odd, I have compiled this version:

```
andrew@skamandros~$ mediainfo --Version
MediaInfo Command line, 
MediaInfoLib - v0.7.35
```

I will admit that I have not ever been a big user of this program but it is certainly a puzzling result. I am a little curious that you got some sound from this file which revealed nothing for me...

Andrew

**[COLOR="Black"]Edit:[/COLOR]** OK I have compiled the very newest:

```

andrew@skamandros~/Desktop$ mediainfo --Version
MediaInfo Command line, 
MediaInfoLib - v0.7.37

```

and this gives the same result:

```

andrew@skamandros~/Desktop$ mediainfo 2010Z1127_1036_0.mpg 
General
Complete name                    : 2010Z1127_1036_0.mpg
Format                           : MPEG-TS
Format/Info                      : Advanced Video Codec
Format profile                   : No PAT/PMT
File size                        : 16.9 MiB
Duration                         : 24s 420ms
Overall bit rate                 : 5 802 Kbps

Video
ID                               : 556 (0x22C)
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Format settings, GOP             : M=4, N=24
**[COLOR="Red"]Duration                         : 24s 420ms[/COLOR]**
Bit rate                         : 5 483 Kbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16:9
Frame rate                       : 50.000 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.119
Stream size                      : 16.0 MiB (95%)
Color primaries                  : BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
Transfer characteristics         : BT.709-5, BT.1361
Matrix coefficients              : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio
ID                               : 606 (0x25E)
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Mode                             : Dual mono
Emphasis                         : 50/15ms
**[COLOR="Red"]Duration                         : 26ms[/COLOR]**
Bit rate mode                    : Constant
Bit rate                         : 32.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Compression mode                 : Lossy
Stream size                      : 104 Bytes (0%)

```

Curious....

---

### Post by mc4man on 2010-12-04
When I Was (am?) thinking your mediainfo was more 'representative it made some sense. Maybe it's just a blip.. (sounds like one

```
mplayer -rawaudio format=0x50 -demuxer rawaudio   /home/doug/Downloads/zinwell-pvr/Record_Video/.2010Z1127_1036_0.mpg
```

---

### Post by zcat on 2010-12-04
> **mc4man said:**
> When I Was (am?) thinking your mediainfo was more 'representative it made some sense. Maybe it's just a blip.. (sounds like one

```
mplayer -rawaudio format=0x50 -demuxer rawaudio   /home/doug/Downloads/zinwell-pvr/Record_Video/.2010Z1127_1036_0.mpg
```

I just copied the files from the zip back into the set top box, and all three clips do have audio. 

Also I've bought and connected a new drive (and zero-wiped the original because it had some bad sectors) since recording those files. There's no chance that the audio is coming from some other hidden file elsewhere on the drive. There's audio in those files somewhere, and multiple sources are telling me it's an HE-AAC stream. There must be a switch for ffmpeg / mplayer to tell them to ignore the (faulty) headers and play the stream correctly? or some way of repairing the headers?

---

### Post by zcat on 2010-12-08
So no other suggestions?

---

### Post by ron999 on 2010-12-08
> **zcat said:**
> So no other suggestions?
No :icon_frown:

The files will play using **ffplay**, but no sound.
Same result using MediaPlayerClassic with K-lite mega codec pack and Windows XP.

---

### Post by vlcplayerfan on 2011-02-09
im from nz and have the same videos as you rec from dvb-t 

play video with sound use vlc player 

to convert video use handbrak

to edit out ads ect after converted use [I]Avidemux

this will work 
[/I]

---

### Post by yurac on 2011-05-21
Hi,

Did you manage to decode the audio?

I have the same issue with dvb-t Israel.

I receive dvb-t using a USB dongle. Several programs are able to display video, including vlc, ffmpeg, me-tv, xbmc. However, the only way I found to make the audio work is using vlc to directly stream the broadcast as follows:

w_scan -X >channels.conf
vlc channels.conf

I also recorded the broadcast to a ts file. Vlc is unable to open that file. Ffmpeg/ffplay and xbmc play that file without audio. Handbrake is able to convert this file to other formats, but again the audio is missing.

There is the tstools package that should be able to handle the ts files. However, for the ts file I recorded it says:
----------------------------------
$ tsinfo sample.ts 
Reading from sample.ts
Scanning 1000 TS packets

Found 0 PAT packets and 0 PMT packets in 1000 TS packets
----------------------------------

So it appears that the file has the basic ts structure, but the contents are somewhat non-standard. Maybe we should post the ts sample to the ffmpeg / mplayer / xbmc community forums and ask them.

Another thing I will try is to trace the vlc run displaying video and audio and attempt to understand how they decode the stream. Note however, that vlc only works well when it owns the channel. It is unable to open a recorded ts file.

Does anyone have any new info regarding that issue?

---

### Post by yurac on 2011-05-21
The issue is solved for me as follows:

I installed XBMC from the pvr branch and tvheadend.
Tvheadend together with xbmc do play the stream correctly - both video and audio. The audio is recognized as AAC.

I still want to take a look on the VLC code to see how the audio stream is decoded.

---

### Post by ahlidap on 2012-05-18
Hi,


I'm having a similar problem with a Video recorded from a Televes 7151 TDT Receiver.

I'm able to play and convert Video, but not the Audio... :(



Mediainfo gives me the info:

```
General
Format                                   : MPEG-TS
Format profile                           : No PAT/PMT
File size                                : 11.8 MiB
Duration                                 : 25s 600ms
Overall bit rate                         : 3 850 Kbps

Video
ID                                       : 768 (0x300)
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Main@L3.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 4 frames
Format settings, GOP                     : M=4, N=28
Duration                                 : 25s 300ms
Bit rate                                 : 3 041 Kbps
Width                                    : 720 pixels
Height                                   : 576 pixels
Display aspect ratio                     : 4:3
Frame rate                               : 25.000 fps
Standard                                 : Component
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Top Field First
Bits/(Pixel*Frame)                       : 0.293
Stream size                              : 9.17 MiB (78%)
Color primaries                          : BT.470-6 System B, BT.470-6 System G, BT.601-6 625, BT.1358 625, BT.1700 625 PAL, BT.1700 625 SECAM
Transfer characteristics                 : BT.470-6 System B, BT.470-6 System G
Matrix coefficients                      : BT.470-6 System B, BT.470-6 System G, BT.601-6 625, BT.1358 625, BT.1700 625 PAL, BT.1700 625 SECAM, IEC 61966-2-4 601

Audio
ID                                       : 769 (0x301)
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format version                           : Version 2
Format profile                           : Main
Muxing mode                              : ADTS
Duration                                 : 25s 600ms
Bit rate mode                            : Constant
Bit rate                                 : 613 Kbps
Channel(s)                               : 4 channels
Channel positions                        : Front: L C R, Side: C
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Delay relative to video                  : -1s 81ms
Stream size                              : 1.87 MiB (16%)
```


Any help with the audio?
Thanks

---

### Post by ahlidap on 2012-05-21
I've shared an example @Ubuntu One.
Here's the link: [http://ubuntuone.com/4M6GHzCjsQP56DiraGdqhb]("http://ubuntuone.com/4M6GHzCjsQP56DiraGdqhb")


with:
```
avplay filename.trp
```

it plays, but only video, with several errors.



PS: some idx files were created by avidemux to try open it.. the importante file is only the trp, i think.



Thanks

---

### Post by shantiq on 2012-05-21
tried to run it with mplayer   and this is what i got  [ image fine no audio]  but the audio shows up on mediainfo 

     puzzling....

```
mplayer 0.trp
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 0.trp.
Detected file format: MPEG-2 transport stream format (libavformat)
[NULL @ 0x7fed21a7d300]non-existing PPS referenced
[h264 @ 0x7fed21a7d300]non-existing PPS 0 referenced
[h264 @ 0x7fed21a7d300]decode_slice_header error
[h264 @ 0x7fed21a7d300]no frame!
[h264 @ 0x7fed21a7d300]non-existing PPS referenced
[h264 @ 0x7fed21a7d300]non-existing PPS 0 referenced
[h264 @ 0x7fed21a7d300]decode_slice_header error
[h264 @ 0x7fed21a7d300]no frame!
[h264 @ 0x7fed21a7d300]non-existing PPS referenced
[h264 @ 0x7fed21a7d300]non-existing PPS 0 referenced
[h264 @ 0x7fed21a7d300]decode_slice_header error
[h264 @ 0x7fed21a7d300]no frame!
[h264 @ 0x7fed21a7d300]non-existing PPS referenced
[h264 @ 0x7fed21a7d300]non-existing PPS 0 referenced
[h264 @ 0x7fed21a7d300]decode_slice_header error
[h264 @ 0x7fed21a7d300]no frame!
[h264 @ 0x7fed21a7d300]non-existing PPS referenced
[h264 @ 0x7fed21a7d300]non-existing PPS 0 referenced
[h264 @ 0x7fed21a7d300]decode_slice_header error
[h264 @ 0x7fed21a7d300]no frame!
[h264 @ 0x7fed21a7d300]non-existing PPS referenced
[h264 @ 0x7fed21a7d300]non-existing PPS 0 referenced
[h264 @ 0x7fed21a7d300]decode_slice_header error
[h264 @ 0x7fed21a7d300]no frame!
[h264 @ 0x7fed21a7d300]non-existing PPS referenced
[h264 @ 0x7fed21a7d300]non-existing PPS 0 referenced
[h264 @ 0x7fed21a7d300]decode_slice_header error
[h264 @ 0x7fed21a7d300]no frame!
[h264 @ 0x7fed21a7d300]non-existing PPS referenced
[h264 @ 0x7fed21a7d300]non-existing PPS 0 referenced
[h264 @ 0x7fed21a7d300]decode_slice_header error
[h264 @ 0x7fed21a7d300]no frame!
[h264 @ 0x7fed21a7d300]mmco: unref short failure
[h264 @ 0x7fed21a7d300]mmco: unref short failure
[h264 @ 0x7fed21a7d300]mmco: unref short failure
[mpegts @ 0x7fed211eb920]max_analyze_duration reached
[mpegts @ 0x7fed211eb920]PES packet size mismatch
[lavf] stream 0: video (h264), -vid 0
VIDEO:  [H264]  720x576  0bpp  50.000 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in .
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
[COLOR="Red"]Audio: no sound
[/COLOR]Starting playback...
[h264 @ 0x7fed21a7d300]reference picture missing during reorder
[h264 @ 0x7fed21a7d300]Missing reference picture
[h264 @ 0x7fed21a7d300]mmco: unref short failure
V:   0.0   0/  0 ??% ??% ??,?% 0 0 
[h264 @ 0x7fed21a7d300]reference picture missing during reorder
[h264 @ 0x7fed21a7d300]Missing reference picture
Movie-Aspect is 1.36:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x576 => 786x576 Planar YV12 
[vdpau] Got display refresh rate 75.025 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.
V:   0.0   0/  0 ??% ??% ??,?% 0 0 
[h264 @ 0x7fed21a7d300]mmco: unref short failure
V:   0.0   0/  0 ??% ??% ??,?% 0 0 
[h264 @ 0x7fed21a7d300]mmco: unref short failure
V:25081.9   0/  0 81% 10%  0.0% 0 0 

Exiting... (Quit)



```

---

### Post by ahlidap on 2012-05-21
> **shantiq said:**
> tried to run it with mplayer   and this is what i got  [ image fine no audio]  but the audio shows up on mediainfo 

     puzzling....




yeah... :/
strange (I think)..

I've tried everything I know... even on paid OS... and nothing!
Maybe this is related with some firmware problem on the TDT Receiver... and there's no update at all.. 

Of course, on receiver the recordings play fine.. but would be great to convert those recordings to other formats...

---

