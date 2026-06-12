---
title: "[SOLVED] Wrong aspect ratio when merging with MP4Box"
date: 2008-12-26
forum: Multimedia Software
---

### Post by mb_webguy on 2008-12-26
I have quite a few HD videos (mkv-h264-mp3) that I'd like to play on my new PS3.  The PS3 doesn't have any problem (I don't think) with h264 video or mp3 audio, but can't handle the matroska container.  So I figured the easiest thing to do would be to use mkvextract to extract the audio and video streams from an mkv file and then use MP4Box to merge them into an mp4.

Overall, it's working fairly well -- it's fast, and I don't have to worry about losing quality through transcoding -- but I'm having one extremely annoying problem: the videos are supposed to have an aspect ratio of 16:9, but when I try to set this using the "-par" option of MP4Box, I get very odd results.  Here are the commands I'm using:```
mkvextract tracks "myfile.mkv" 1:"myfile.h264" 2:"myfile.mp3"
MP4Box -add "myfile.h264" -add "myfile.mp3" -fps 25 -par 1=16:9 "myfile.mp4"
```If I change the "-par" option of the second command to "none", I get an aspect ratio 1.25:1 when I play the file in VLC -- which is actually what I'd expect, with 720x576 and square pixels.  But setting par to 4:3 results an aspect ratio being set at 1.667:1, setting par to 16:9 results in an actual aspect ratio of 2.22:1 (and no, I *don't* mean 2.21:1), setting par to 16:10 results in an actual aspect ratio of 2:1, setting par to 2.21:1 results in an actual aspect ratio of 5:4, and setting par to 5:4 results in an actual aspect ratio of 1.562:1...  

Since the actual aspect ratios aren't progressively larger, and since some of those aren't even standard aspect ratios, it's apparently not that MP4Box is just bumping me up from whatever I specify to the next wider aspect ratio...  I'm stumped.  Help!

P.S. -- While I think that if I could get this working that it would be the fastest way to do what I'm trying to do, if anyone knows of another way to quickly and easily convert an mkv to an mp4 without transcoding, I'd definitely be willing to try different methods.

P.P.S -- Just in case it might be helpful, here's the mediainfo output for the original mkv file I'm currently trying to convert.```
General
Complete name                    : /mnt/Multimedia/Television/Doctor Who/Doctor Who - s01e01 - Rose.mkv
Format                           : Matroska
File size                        : 351 MiB
Duration                         : 44mn 15s
Overall bit rate                 : 1 108 Kbps
Movie name                       : Done with AutoMKV 0.82 http://forum.doom9.org/showthread.php?p=854221 
Encoded date                     : UTC 2007-06-22 10:13:39
Writing application              : mkvmerge v2.0.2 ('You're My Flame') built on Feb 21 2007 23:40:55
Writing library                  : libebml v0.7.7 + libmatroska v0.8.1

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L5.1
Format settings, CABAC           : Yes
Format settings, ReFrames        : 16 frames
Muxing mode                      : Container profile=Unknown@5.1
Codec ID                         : V_MPEG4/ISO/AVC
Duration                         : 44mn 15s
Bit rate                         : 902 Kbps
Nominal bit rate                 : 951 Kbps
Width                            : 720 pixels
Height                           : 576 pixels
Display aspect ratio             : 16/9
Frame rate                       : 25.000 fps
Standard                         : PAL
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.092
Title                            : Doctor Who S01E01
Writing library                  : x264 core 55 svn-656
Encoding settings                : cabac=1 / ref=16 / deblock=1:-2:-1 / analyse=0x3:0x133 / me=umh / subme=6 / brdo=1 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / chroma_qp_offset=0 / threads=2 / nr=0 / decimate=1 / mbaff=0 / bframes=3 / b_pyramid=1 / b_adapt=1 / b_bias=0 / direct=3 / wpredb=1 / bime=1 / keyint=250 / keyint_min=25 / scenecut=40(pre) / rc=2pass / bitrate=951 / ratetol=1.0 / rceq='blurCplx^(1-qComp)' / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / ip_ratio=1.40 / pb_ratio=1.30

Audio
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Codec ID                         : A_MPEG/L3
Codec ID/Hint                    : MP3
Duration                         : 44mn 15s
Bit rate mode                    : Variable
Bit rate                         : 153 Kbps
Minimum bit rate                 : 160 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Writing library                  : LAME3.97 
Encoding settings                : ABR

```

---

### Post by mb_webguy on 2008-12-26
I don't normally bump a thread in under 24 hours, but it's been over 10 hours with no comments, and the thread had slipped to page 3.  It seems like there should be a simple solution to this problem.  Surely someone here has some advice...?

---

### Post by xc3RnbFO8P on 2008-12-26
Try Avidemux, Auto PSP (H264).

---

### Post by mb_webguy on 2008-12-26
I'm fairly familiar with Avidemux...  That's actually the first thing I tried before trying the mkvextract/MP4Box method.  The Auto options don't seem to do anything -- none of the settings change.  While I've tried setting the options manually, I can't find any way to set the PAR, and the aspect ratio defaults to 1.25:1 just as when I use "none" for the value of the -par option of MP4Box.

---

### Post by mb_webguy on 2008-12-26
I think I figured it out...  On a hunch, I tried a value for -par of 64:45, and the resulting mp4 has the correct aspect ratio of 16:9!  "PAR" apparently sets the aspect ratio of the pixels, and not the video.  On hindsight, I should have read the documentation for MP4Box a bit more carefully, since "par" is apparently short for "*pixel* aspect ratio".

Since the video has a square-pixel aspect ratio of 1.25:1, and the desired aspect ratio is 16:9, I divided 16/9 by 1.25, which is how I arrived at the 64:45 figure.  That seems like an awkward way to arrive at the correct video aspect ratio, but... whatever works.

Problem solved.

And if anyone else has been trying to convert some mkv files to mp4, this is definitely one of the easiest and quickest ways I've found so far -- assuming, of course, that the mkv contains video and audio supported by the mp4 container and your device (PS3, Xbox360, etc.).

---

### Post by blue13130 on 2009-01-02
Thanks for posting your question and posting your solutions.  I have been having problems with the aspect ratio when I convert an mkv file to mp4 using mkvextract and MP4Box.  I have set the PAR to be the wanted aspect ratio divided by the pixel width and height of the movie and the resulting mp4 file comes out perfect.

For example wanted a 16/9 end file and movie dimensions are w x h 960x704
PAR=(16/9)/(960/704)
PAR=16/9x704/960
PAR=11264/8640

MP4Box -fps 23.976 -add video.264 -add audio.aac -par 1=11264:8640 movie.mp4

Resulting file is correct 16/9 aspect ratio when played by mplayer or streamed to PS3 via mediatomb.

Thanks for your help!

---

### Post by rodrigopolo on 2011-08-15
Here is a handy calculator to fix the aspect ratio of an image with the PAR using MP4Box
[http://tools.rodrigopolo.com/mp4box_aspect_fix/](http://tools.rodrigopolo.com/mp4box_aspect_fix/)

---

