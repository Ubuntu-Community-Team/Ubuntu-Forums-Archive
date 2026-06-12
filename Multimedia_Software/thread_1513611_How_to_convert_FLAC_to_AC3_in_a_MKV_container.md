---
title: "How to convert FLAC to AC3 in a MKV container"
date: 2010-06-19
forum: Multimedia Software
---

### Post by jabalsad on 2010-06-19
Hi all,

I simply want to change the codec of the audio stream used in a mkv file. I've tried mencoder and ffmpeg but no love. It might be that I'm not doing it right :/

Basically, I want the video stream to stay the same (i.e. -vcodec copy) and I want the audio stream to be converted from FLAC to AC3. 

What is the easiest way to go about doing this?

---

### Post by ron999 on 2010-06-19
Hi
I suppose the easiest way is to try again with ffmpeg.
Like this:-
```
ffmpeg -i movie.mkv -vcodec copy -acodec ac3 -ab 384kb -ar 48000 -ac 2 new_movie.mkv
```

---

### Post by jabalsad on 2010-06-26
Many thanks for the feedback. I had to add the following parameter due to the subtitles: -scodec copy. I then get the following output:

```

# ffmpeg -i eden.mkv -vcodec copy -acodec ac3 -ab 384kb -ar 48000 -ac 2 -scodec copy new_movie.mkv
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, matroska, from 'eden.mkv':
  Duration: 01:21:32.88, start: 0.000000, bitrate: N/A
    Stream #0.0(jpn): Video: h264, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(jpn): Audio: flac, 48000 Hz, 5.1, s16
    Stream #0.2(eng): Subtitle: 0x0000
    Stream #0.3: Attachment: 0x0000
File 'new_movie.mkv' already exists. Overwrite ? [y/N] y
Output #0, matroska, to 'new_movie.mkv':
    Stream #0.0(jpn): Video: 0x0000, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], q=2-31, 90k tbn, 1k tbc
    Stream #0.1(jpn): Audio: ac3, 48000 Hz, stereo, s16, 384 kb/s
    Stream #0.2(eng): Subtitle: 0x0000
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
  Stream #0.2 -> #0.2
[matroska @ 0x1a526c0]Codec for stream 2 does not use global headers but container format requires global headers
Press [q] to stop encoding
Resampling with input channels greater than 2 unsupported.
Can not resample 6 channels @ 48000 Hz to 2 channels @ 48000 Hz

```

---

### Post by jabalsad on 2010-06-26
So I changed the parameter -ac 2 to -ac 6 and then I get:

```

...
[matroska @ 0x16486c0]Codec for stream 2 does not use global headers but container format requires global headers
Press [q] to stop encoding
Multiple frames in a packet from stream 1
[NULL @ 0x1496590]error, non monotone timestamps 375 >= 334
av_interleaved_write_frame(): Error while opening file

```

---

### Post by benmoran on 2010-06-26
If you can't get that to work, try Avidemux. It's in the repos.

---

### Post by jabalsad on 2010-06-26
> **benmoran said:**
> If you can't get that to work, try Avidemux. It's in the repos.

I'll give it a try, thanks.

---

### Post by jabalsad on 2010-06-26
Seems like avidemux does not support FLAC audio:

[http://www.avidemux.org/admWiki/doku.php?id=general:audio_decoders](http://www.avidemux.org/admWiki/doku.php?id=general:audio_decoders)

Can anyone recommend any other apps that may perform this task?

---

### Post by jabalsad on 2010-06-26
So I have at least extracted the FLAC stream from the mkv by installing mkvtoolnix and running

```

mkvmerge -i movie.mkv
mkvextract tracks movie.mkv 2:movie.flac

```

The tool recognizes it as an OGG codec inside the FLAC container.

---

### Post by ron999 on 2010-06-26
This is getting complicated.
Maybe you could use **mediainfo** program to find out just what is in that mkv file.

---

### Post by jabalsad on 2010-06-26
Pretty much what I expected:

```


# mediainfo eden.mkv
General
Complete name                    : eden.mkv
Format                           : Matroska
File size                        : 1.34 GiB
Duration                         : 1h 21mn
Overall bit rate                 : 2 351 Kbps
Encoded date                     : UTC 2010-04-10 21:45:30
Writing application              : mkvmerge v3.3.0 ('Language') built on Mar 24 2010 14:59:24
Writing library                  : libebml v0.8.0 + libmatroska v0.9.0
Cover                            : Yes

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L5.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 16 frames
Muxing mode                      : Container profile=Unknown@5.0
Codec ID                         : V_MPEG4/ISO/AVC
Duration                         : 1h 21mn
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16:9
Frame rate                       : 23.976 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Writing library                  : x264 core 92 r1523 25ca5b0
Encoding settings                : cabac=1 / ref=16 / deblock=1:-2:-2 / analyse=0x3:0x133 / me=umh / subme=10 / psy=1 / psy_rd=0.80:0.00 / mixed_ref=1 / me_range=32 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=0 / chroma_qp_offset=-2 / threads=6 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / constrained_intra=0 / bframes=8 / b_pyramid=2 / b_adapt=2 / b_bias=0 / direct=3 / wpredb=1 / wpredp=1 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=crf / mbtree=1 / crf=16.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00
Language                         : Japanese

Audio
ID                               : 2
Format                           : FLAC
Format/Info                      : Free Lossless Audio Codec
Codec ID                         : A_FLAC
Duration                         : 1h 21mn
Bit rate mode                    : Variable
Channel(s)                       : 6 channels
Sampling rate                    : 48.0 KHz
Bit depth                        : 16 bits
Writing library                  : libFLAC 1.2.1 (UTC 2007-09-17)
Language                         : Japanese

Text
ID                               : 3
Format                           : ***
Codec ID                         : S_TEXT/***
Codec ID/Info                    : Advanced Sub Station Alpha
Language                         : English

```

---

### Post by ron999 on 2010-06-26
OK
The flac channel that you've already extracted from the mkv, unpack it to wav using command:-
```
flac -d movie.flac
```

When you've finished you should have a file named **movie.wav**.
Use mediainfo to confirm that it's 6 channel audio in the wav file.

---

### Post by jabalsad on 2010-06-26
Okay so I think i might have figured this out (lol).

1) use mkvextract to extract the flac stream.
2) use ffmpeg to convert the newly created flac file to ac3
3) use mkvmerge to combine the new ac3 stream with the video and subtitle stream from the original file.

Running it now, here's hoping to success \o/

---

### Post by jabalsad on 2010-06-26
Whoohoo! Success :D

It plays back fine and everything. Now I can finally load this video on my Popcorn Hour because it doesn't support FLAC inside MKV playback >_>

```

# mediainfo new.mkv
General
Complete name                    : new.mkv
Format                           : Matroska
File size                        : 904 MiB
Duration                         : 1h 21mn
Overall bit rate                 : 1 550 Kbps
Encoded date                     : UTC 2010-06-26 18:24:52
Writing application              : mkvmerge v3.0.0 ('Hang up your Hang-Ups') built on Dec 29 2009 00:21:20
Writing library                  : libebml v0.7.7 + libmatroska v0.8.1
Cover                            : Yes

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L5.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 16 frames
Muxing mode                      : Container profile=Unknown@5.0
Codec ID                         : V_MPEG4/ISO/AVC
Duration                         : 1h 21mn
Bit rate                         : 1 135 Kbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16:9
Frame rate                       : 23.976 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.051
Stream size                      : 662 MiB (73%)
Writing library                  : x264 core 92 r1523 25ca5b0
Encoding settings                : cabac=1 / ref=16 / deblock=1:-2:-2 / analyse=0x3:0x133 / me=umh / subme=10 / psy=1 / psy_rd=0.80:0.00 / mixed_ref=1 / me_range=32 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=0 / chroma_qp_offset=-2 / threads=6 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / constrained_intra=0 / bframes=8 / b_pyramid=2 / b_adapt=2 / b_bias=0 / direct=3 / wpredb=1 / wpredp=1 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=crf / mbtree=1 / crf=16.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00
Language                         : Japanese

Audio
ID                               : 3
Format                           : AC-3
Format/Info                      : Audio Coding 3
Mode extension                   : CM (complete main)
Codec ID                         : A_AC3
Duration                         : 1h 21mn
Bit rate mode                    : Constant
Bit rate                         : 384 Kbps
Channel(s)                       : 6 channels
Channel positions                : Front: L C R, Side: L R, LFE
Sampling rate                    : 48.0 KHz
Stream size                      : 224 MiB (25%)

Text
ID                               : 2
Format                           : ***
Codec ID                         : S_TEXT/***
Codec ID/Info                    : Advanced Sub Station Alpha
Language                         : English

```

---

### Post by ron999 on 2010-06-26
That's good.
What command did you use to convert the flac file to ac3?

---

### Post by jabalsad on 2010-06-26
```

ffmpeg -i movie.flac -acodec ac3 -ab 384kb -ar 48000 -ac 6 movie.ac3

```

It was spitting out a lot of weird messages, but it still seemed fine.

---

### Post by ron999 on 2010-06-26
OK, thanks.
Your method in post #12 is very logical once you've determined what's inside the mkv file.
:guitar:

---

### Post by jabalsad on 2010-06-26
Too bad PCH still can't play the file ~_~

I'm trying PCM now.

---

