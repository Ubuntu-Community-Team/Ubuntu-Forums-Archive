---
title: "No video on ps3"
date: 2010-08-14
forum: Multimedia Software
---

### Post by aryan22 on 2010-08-14
I'm trying to convert my mkv file to mp4, so that i can watch i on my ps3...
Of course this did not work for me, The audio worked but the video did not...
so I just re-encoded it to a divx file (don't like to hardsub video)...
But I would like to know what I'm doing wrong anyway...
You know, for the sake of knowledge and all that.
and also, re-encoding takes a lot of time, so I'd like to avoid it if possible.

anyway, here's what's going on.

My MKV File.

```
File 'main-file.mkv': container: Matroska
Track ID 1: video (V_MPEG4/ISO/AVC)
Track ID 2: audio (A_VORBIS)
Track ID 3: subtitles (S_TEXT/***)
Track ID 4: subtitles (S_TEXT/UTF8)
Attachment ID 1: type 'application/x-truetype-font', size 22124 bytes, file name 'Wunderlich-Medium.otf'
Attachment ID 2: type 'application/x-truetype-font', size 59688 bytes, file name 'Calligraphic-810-BT.ttf'
Chapters: 5 entries
```I'm cool with watching unstyled subtitles,
so I don't extract them.

```
mkvextract tracks main-file.mkv 1:vid.h264 2:aud.ogg 4:sub.srt
```Now, let's get to know our video file a little better...

```
mediainfo vid.h264
```here's the output

```
General
Complete name                    : vid.h264
Format                           : AVC
Format/Info                      : Advanced Video Codec
File size                        : 311 MiB

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L5.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 12 frames
Bit rate                         : 1 772 Kbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16:9
Frame rate                       : 23.976 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.080
Writing library                  : x264 core 67 r1134M b8808bf
Encoding settings                : cabac=1 / ref=12 / deblock=1:0:0 / analyse=0x1:0x131 / me=umh / subme=6 / psy_rd=1.0:0.0 / mixed_ref=1 / me_range=20 / chroma_me=1 / trellis=2 / 8x8dct=0 / cqm=0 / deadzone=21,11 / chroma_qp_offset=-2 / threads=6 / nr=0 / decimate=1 / mbaff=0 / bframes=8 / b_pyramid=1 / b_adapt=1 / b_bias=0 / direct=1 / wpredb=1 / keyint=250 / keyint_min=25 / scenecut=40 / rc=2pass / bitrate=1772 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / ip_ratio=1.40 / pb_ratio=1.30 / aq=1:0.80
```As most of you know, ps3 does not support level 5.0 or 5.1 h264 files...
so we open the file in hexedit and replace "67 4D 40 32" with "67 4D 40 29"...
Let's check if it worked...
"mediainfo vid.h264" gives us the same thing with a difference in...

```
Format profile                   : Main@L4.1
```so that takes care of our video.
now for the audio.

```
oggdec aud.ogg
faac -b 128 aud.wav
```audio taken care of too...
now for the mp4 container...

```
MP4Box -add vid.h264 -fps 23.976 -add aud.aac -add sub.srt -new conv.mp4
MP4Box -hint conv.mp4
```This works just fine if i play it in vlc, but I get only audio when playing in ps3.
So, i try to do the same thing with mp4creator.

```
mp4creator -c vid.h264 -r 23.976 conv.mp4
mp4creator -c aud.aac conv.mp4
mp4creator -optimize conv.mp4
mp4creator -hint=1 conv.mp4
mp4creator -hint=2 conv.mp4
```on hint=1 i got an error saying.

```
MP4ERROR: MP4File::FindIntegerProperty: no such property - moov.trak[0].mdia.minf.stbl.stsd.*.esds.decConfigDescr.objectTypeId
MP4ERROR: MP4File::FindIntegerProperty: no such property - moov.trak[2].mdia.minf.stbl.stsd.*.esds.decConfigDescr.objectTypeId
```and a similar one on hint=2.

```
MP4ERROR: MP4File::FindIntegerProperty: no such property - moov.trak[0].mdia.minf.stbl.stsd.*.esds.decConfigDescr.objectTypeId
MP4ERROR: MP4File::FindIntegerProperty: no such property - moov.trak[2].mdia.minf.stbl.stsd.*.esds.decConfigDescr.objectTypeId
MP4ERROR: MP4File::FindIntegerProperty: no such property - moov.trak[3].mdia.minf.stbl.stsd.*.esds.decConfigDescr.objectTypeId
```On researching, I found that I'm not the only one getting this error...
but unfortunately most just ignored it coz they had no problem...
and some had a problem streaming their video, but went unsolved.

I'm at a complete loss here.
Any help would be really appreciated.

---

