---
title: "Errors converting video, flv to 3gp"
date: 2009-12-08
forum: Multimedia Software
---

### Post by pooja on 2009-12-08
Hi everyone,
I have a 700kb flv video on my Ub. 9.10 Desktop and want to convert it to 3gp format with 176x144 video resolution and 15 fps in order to view it properly on my Nokia phone. 
I have downloaded via Synaptic Packet Manager the following packages: ffmpeg, lame, amrwb, amrnb. 
When I give this command:
```
ffmpeg -i MacVSPc.flv -r 15 -s 176x144 MacVSPC.3gp

``` 
I get back:
```


Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'MacVSPc.flv':
  Duration: 00:00:28.06, start: 0.000000, bitrate: 209 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 145 kb/s, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
File 'MacVSPC.3gp' already exists. Overwrite ? [y/N] y

Output #0, 3gp, to 'MacVSPC.3gp':
    Stream #0.0: Video: h263, yuv420p, 176x144, q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: 0x0000, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

```

What does it mean with "Unsupported codec for output stream #0.1"?
Do I have to install additional packages to get the video converted into 3gp?

---

### Post by SuperSonic4 on 2009-12-08
It means ffmpeg has been compiled without mp3 support - probably due to patent issues. I think you can install libavcodec-unstripped or similar and it should/might work

What is the output of 
```
ffmpeg -i MacVSPc.flv -r 15 -s 176x144 -acodec libvorbis MacVSPC.3gp
```

and

```
ffmpeg -i MacVSPc.flv -r 15 -s 176x144 -acodec libfaac MacVSPC.3gp
```

you may want to test these on your phone since 3gp is a container format

---

### Post by FakeOutdoorsman on 2009-12-08
> **SuperSonic4 said:**
> It means ffmpeg has been compiled without mp3 support - probably due to patent issues.
It's more likely that FFmpeg, by default, selects an AMR encoder when .3gp is the output, but in this case there is none available.
> **SuperSonic4 said:**
> I think you can install libavcodec-unstripped or similar and it should/might work
The **libavcodec-extra-52** package for Karmic does enable restricted encoders, but unfortunately it does not include *libfaac* or an AMR encoder.
> **SuperSonic4 said:**
> What is the output of 
```
ffmpeg -i MacVSPc.flv -r 15 -s 176x144 -acodec libvorbis MacVSPC.3gp
```
Vorbis audio is probably not an accepted audio format for 3GP.  It accepts several variants of AMR and AAC.
> **SuperSonic4 said:**
> ```
ffmpeg -i MacVSPc.flv -r 15 -s 176x144 -acodec libfaac MacVSPC.3gp
```
There is no libfaac available for FFmpeg from the Ubuntu Karmic 9.10 repository.  You have two choices if you want to use FFmpeg to encode a 3gp file:
[list][*] Compile FFmpeg yourself and use the libopencore* or libfaac to encode the audio: [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095), or
[*] Wait about a week and Medibuntu will most likely release a [s]FFmpeg version[/s] version of libavcodec for FFmpeg.[/list]

---

### Post by pooja on 2009-12-09
Hi,
Thank you both for replying. I read the "HOWTO" guide FakeOutdoorsman linked me up to. Installed x264 but it didn't seem to work for me: the output was created, output.3gp, audio was fantastic but no video could be seen once transferred to the phone. 
```
ffmpeg -i MacVSPc.flv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -s 176x144 -r 15 -crf 22 -threads 0 output.3

```

I did some tweaking, still nothing new. So I tried giving the old command:
```
ffmpeg -i MacVSPc.flv -acodec libfaac -ab 8.85k -ac 1 -ar 16000 -vcodec h263 -s qcif -r 15 output.3gp
```

This time, once the video was in the phone, I could view it properly (was not a black screen) but the audio was poor. I decided to combine the two commands in this way:
```
ffmpeg -i MacVSPc.flv  -acodec libfaac -ab 128k -ac 2 -vcodec h263 -s qcif -r 15 OUTPUT.3gp
```
This time, once transferred to the phone, the video was of a good quality, both audio and video wise. However I got this response as part of the processing:

```
FFmpeg version SVN-r20785, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Dec  9 2009 19:27:47 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 5. 1 / 50. 5. 1
  libavcodec    52.43. 0 / 52.43. 0
  libavformat   52.41. 0 / 52.41. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 2 /  0. 7. 2
[flv @ 0x9255380]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'MacVSPc.flv':
  Duration: 00:00:28.06, start: 0.000000, bitrate: 209 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 145 kb/s, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, 1 channels, s16, 64 kb/s
  Metadata
    duration        : 28
    starttime       : 0
    totalduration   : 28
    width           : 320
    height          : 240
    videodatarate   : 142
    audiodatarate   : 64
    totaldatarate   : 215
    framerate       : 30
    bytelength      : 754196
    canseekontime   : true
    sourcedata      : B4A7D0384HH
    purl            : 
    pmsg            : 
Output #0, 3gp, to 'output2.3gp':
    Stream #0.0: Video: h263, yuv420p, 176x144, q=2-31, 200 kb/s, 15 tbn, 15 tbc
    Stream #0.1: Audio: aac, 22050 Hz, 2 channels, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[h263 @ 0x92d3010]warning, clipping 1 dct coefficients to -127..127
    Last message repeated 22 times  243kB time=11.98 bitrate= 166.4kbits/s    
[h263 @ 0x92d3010]warning, clipping 2 dct coefficients to -127..127
[h263 @ 0x92d3010]warning, clipping 1 dct coefficients to -127..127kbits/s    
frame=  423 fps=357 q=2.0 Lsize=     718kB time=28.00 bitrate= 210.0kbits/s    
video:485kB audio:224kB global headers:0kB muxing overhead 1.298311%

```

This last line: [FONT="Courier New"]**video:485kB audio:224kB global headers:0kB muxing overhead 1.298311%**[/FONT], is it anything serious? Is there a better way to give the encoding command?

---

### Post by SuperSonic4 on 2009-12-09
> **pooja said:**
> Hi,
Thank you both for replying. I read the "HOWTO" guide FakeOutdoorsman linked me up to. Installed x264 but it didn't seem to work for me: the output was created, output.3gp, audio was fantastic but no video could be seen once transferred to the phone. 
```
ffmpeg -i MacVSPc.flv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -s 176x144 -r 15 -crf 22 -threads 0 output.3

```

You didn't specify a video codec nor told it to copy video so ffmpeg didn't ;)

> I did some tweaking, still nothing new. So I tried giving the old command (see my 1st post):
```
ffmpeg -i MacVSPc.flv -acodec libfaac -ab 8.85k -ac 1 -ar 16000 -vcodec h263 -s qcif -r 15 output.3gp
```

This time, once the video was in the phone, I could view it properly (was not a black screen) but the audio was poor

I'd be very surprised if **8.85**kbps mono wasn't poor! :p CD quality is 128kbps and radio is 96kbps

> . I decided to combine the two commands in this way:
```
ffmpeg -i MacVSPc.flv  -acodec libfaac -ab 128k -ac 2 -vcodec h263 -s qcif -r 15 OUTPUT.3gp
```
This time, once transferred to the phone, the video was of a good quality, both audio and video wise. However I got this response as part of the processing:

```
FFmpeg version SVN-r20785, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Dec  9 2009 19:27:47 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 5. 1 / 50. 5. 1
  libavcodec    52.43. 0 / 52.43. 0
  libavformat   52.41. 0 / 52.41. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 2 /  0. 7. 2
[flv @ 0x9255380]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'MacVSPc.flv':
  Duration: 00:00:28.06, start: 0.000000, bitrate: 209 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 145 kb/s, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, 1 channels, s16, 64 kb/s
  Metadata
    duration        : 28
    starttime       : 0
    totalduration   : 28
    width           : 320
    height          : 240
    videodatarate   : 142
    audiodatarate   : 64
    totaldatarate   : 215
    framerate       : 30
    bytelength      : 754196
    canseekontime   : true
    sourcedata      : B4A7D0384HH
    purl            : 
    pmsg            : 
Output #0, 3gp, to 'output2.3gp':
    Stream #0.0: Video: h263, yuv420p, 176x144, q=2-31, 200 kb/s, 15 tbn, 15 tbc
    Stream #0.1: Audio: aac, 22050 Hz, 2 channels, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[h263 @ 0x92d3010]warning, clipping 1 dct coefficients to -127..127
    Last message repeated 22 times  243kB time=11.98 bitrate= 166.4kbits/s    
[h263 @ 0x92d3010]warning, clipping 2 dct coefficients to -127..127
[h263 @ 0x92d3010]warning, clipping 1 dct coefficients to -127..127kbits/s    
frame=  423 fps=357 q=2.0 Lsize=     718kB time=28.00 bitrate= 210.0kbits/s    
video:485kB audio:224kB global headers:0kB muxing overhead 1.298311%

```

This last line: [FONT="Courier New"]**video:485kB audio:224kB global headers:0kB muxing overhead 1.298311%**[/FONT], is it anything serious? Is there a better way to give the encoding command?

If there was no error message than all is good

---

### Post by V. Wayne on 2010-03-12
Try this for better audio:

ffmpeg -i video_in.flv -acodec libfaac -ab 12.65k -ac 1 -ar 16000 -vcodec h263 -s qcif -r 15 video_out.3gp

---

