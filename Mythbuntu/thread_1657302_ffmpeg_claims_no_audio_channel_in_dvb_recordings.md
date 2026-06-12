---
title: "ffmpeg claims no audio channel in dvb recordings"
date: 2011-01-01
forum: Mythbuntu
---

### Post by reformy on 2011-01-01
Hi
I m trying to transcode a recording I did on my mythbuntu's DVB recorder. I m using ffmpeg:
```
ffmpeg -i mpg.mpg -s 480x360 -b 248k -f mp4 -acodec libfaac -ar 24000 -ab 65535 mpg.mp4
```
I get no audio channel on the input file:
```
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
[h264 @ 0x8c9cfa0]number of reference frames exceeds max (probably corrupt input), discarding one
    Last message repeated 53 times
[h264 @ 0x8c9cfa0]mmco: unref short failure
Input #0, mpegts, from 'mpg.mpg':
  Duration: 01:03:00.68, start: 26428.262689, bitrate: 97 kb/s
  Program 1
    Stream #0.0[0xa41]: Video: h264, yuv420p, 720x576 [PAR 12:11 DAR 15:11], 50 tbr, 90k tbn, 50 tbc
    Stream #0.1[0xa50](heb): Subtitle: dvbsub
    Stream #0.2[0xa51](rus): Subtitle: dvbsub
    Stream #0.3[0xa52](ara): Subtitle: dvbsub

```

And the output file is transcoded with no audio.
Why is that? What am I missing?

Thanks
Yair

---

### Post by reformy on 2011-01-02
I've opened the mpg file in GSpot:
```
File Type: MPEG-2 Transport Stream
Mime Type: video/mp2t
```
How can I transcode the audio from an mp2t file?
or - can I change the DVB-T card setting and make it use some other codec?

---

### Post by BicyclerBoy on 2011-01-02
The dvb tuner cards output data streams un-decoded.
This can not & does not need to be changed.
Only analogue tuner cards compress/change video data.

dvb-t uses mpeg2-ts container that allows MPEG-4/10 H264 AVC etc.

What version of ffmpeg are you using ? You seem to have cut that off...
Old versions not patched do not work with LATM_AAC LOAS commonly used with dvb-t.

Did you cut off any other streams as well ?
The video & audio streams can be in any order/position.

ffmpeg changes its command line options like underwear..

If you see any audio streams they can be selected by -map 0:0 -map 0:4  select streams 0 & 4 for output file (thru' codec etc) 

Try setting channel count by option -ac 2 .

---

### Post by reformy on 2011-01-03
Thanks BicyclerBoy,
I've included all the streams lines in the output, of course. There is no audio channel (but when I play a recoding in the frontend I have audio).
The ffmpeg version should be the latest from medibuntu:
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.

Do you think I need some other ffmpeg version?
I'll try my window's ffmpeg too maybe.

---

### Post by nickrout on 2011-01-03
> **reformy said:**
> Thanks BicyclerBoy,
I've included all the streams lines in the output, of course. There is no audio channel (but when I play a recoding in the frontend I have audio).
The ffmpeg version should be the latest from medibuntu:
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.

Do you think I need some other ffmpeg version?
I'll try my window's ffmpeg too maybe.

give us the mediainfo output for the file:

```
sudo add-apt-repository ppa:shiki/mediainfo 
sudo aptitude update
sudo aptitude install mediainfo
mediainfo mpg.mpg
```

---

### Post by reformy on 2011-01-03
```
General
ID                               : 2
Complete name                    : mpg.mpg
Format                           : MPEG-TS
File size                        : 43.9 MiB
Duration                         : 3mn 28s
Overall bit rate                 : 1 771 Kbps

Video
ID                               : 2625 (0xA41)
Menu ID                          : 1 (0x1)
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Duration                         : 3mn 27s
Width                            : 720 pixels
Height                           : 576 pixels
Display aspect ratio             : 4:3
Frame rate                       : 25.000 fps
Standard                         : Component
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Interlaced
Scan order                       : Top Field First
Color primaries                  : BT.470-6 System B, BT.470-6 System G, BT.601-6 625, BT.1358 625, BT.1700 625 PAL, BT.1700 625 SECAM
Transfer characteristics         : BT.470-6 System B, BT.470-6 System G
Matrix coefficients              : BT.470-6 System B, BT.470-6 System G, BT.601-6 625, BT.1358 625, BT.1700 625 PAL, BT.1700 625 SECAM, IEC 61966-2-4 601

Audio
ID                               : 2626 (0xA42)
Menu ID                          : 1 (0x1)
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Duration                         : 3mn 28s
Video delay                      : -990ms

Text
ID                               : 2640 (0xA50)
Menu ID                          : 1 (0x1)
Format                           : DVB Subtitles
Language                         : Hebrew

```

I guess we can see the audio here. Why can't ffmpeg see it?

---

### Post by nickrout on 2011-01-03
maybe your version of ffmpeg does not support aac audio?

---

### Post by FakeOutdoorsman on 2011-01-03
Maybe a more recent version of FFmpeg will be able to decode the audio. Development is very active and bug fixes come often.

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

If you don't want to compile FFmpeg you could share the file and I can take a look at it.

---

### Post by reformy on 2011-01-14
> **FakeOutdoorsman said:**
> Maybe a more recent version of FFmpeg will be able to decode the audio. Development is very active and bug fixes come often.

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)


Thanks! That worked. Now I see the audio channel of the input file in the stdout.

---

