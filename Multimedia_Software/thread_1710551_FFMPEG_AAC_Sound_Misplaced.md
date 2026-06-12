---
title: "FFMPEG AAC Sound Misplaced"
date: 2011-03-20
forum: Multimedia Software
---

### Post by Alan James on 2011-03-20
I am converting a lot of videos through FFMPEG using X264 and AAC as the codecs. Some videos have mono sound, some have 2 channels, and some have 5.1. I compiled FFMPEG from source so the codecs are installed correctly but I keep getting an error with 5.1 sound. After the conversion the video plays the sound that should come from the center speak through the right. I tried libfaac and the experimental aac codec inside FFMPEG and both give me the same error.

How can I fix this?

---

### Post by FakeOutdoorsman on 2011-03-20
You might have to use something other than FFmpeg to deal with the channels properly. Can you show the complete FFmpeg console output for an input with 5.1 channels of audio?
```
ffmpeg -i input.foo
```

---

### Post by Alan James on 2011-03-20
Here is the output of the file giving me the most problems.

```
FFmpeg version git-N-28456-g1c31b26, Copyright (c) 2000-2011 the FFmpeg developers
  built on Mar 17 2011 12:49:56 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    50. 39. 0 / 50. 39. 0
  libavcodec   52.114. 0 / 52.114. 0
  libavformat  52.103. 0 / 52.103. 0
  libavdevice  52.  3. 0 / 52.  3. 0
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[matroska,webm @ 0x1a96650] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from '11.mkv':
  Duration: 00:01:04.39, start: 0.000000, bitrate: 1536 kb/s
    Stream #0.0(eng): Video: h264 (High), yuv420p, 1920x816 [PAR 1:1 DAR 40:17], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: dca (DTS), 48000 Hz, 5.1, s16, 1536 kb/s (default)
At least one output file must be specified
```

---

### Post by FakeOutdoorsman on 2011-03-20
By default FFmpeg seems to attempt a downmix from 5.1 to 2 channels:
```
$ ffmpeg -i VTS_02_1.VOB -acodec libfaac -aq 100 -vn -map 0:10 out.mp4
...
Stream #0.10[0x89]: Audio: dca (DTS), 48000 Hz, 5.1, s16, 768 kb/s
...
Stream #0.0: Audio: libfaac, 48000 Hz, stereo, s16, 64 kb/s
Input stream #0.10 frame changed from rate:48000 fmt:s16 ch:6 to rate:48000 fmt:s16 ch:2
```
For these inputs you could try adding *-ac 6*. I only have headphones so I can't really test the output.

---

### Post by Alan James on 2011-03-20
Adding -ac 6 doesn't seem to make a difference. Adding -ac 2 converts all the videos to 2 channels, which kinda solves the problem, but its not ideal.

I think the its a bug in FFMPEG. I have been looking for a patch to fix this or even a bug report to confirm my suspicions but so far I have found nothing. In fact today when I searched for a solution in Google the first result was this thread.

Have any suggestions on where I can turn to fix this problem?

---

### Post by Alan James on 2011-03-21
I'm finding now that I am having a lot of problems. libfaac and the experimental aac share the same problems, but libfaac has a few extra errors. The shared problems are the concern however.

Mono to 2 - If I don't manually up convert mono to 2 channels FFMPEG just hangs and won't do anything.
5.1 to 5.1 - 5.1 audio doesn't properly get converted to 5.1 AAC. The channels get mixed up, but I can convert some to 2 channels.
5.1 to 2 - Some 5.1 audio isn't compatible with down converting to 2 channels &#8220;Resampling with input channels greater than 2 unsupported.&#8221;

If setting everything to 2 channels worked all the time I would use that but it doesn't. Basically I'm trying to find a setting that works with all audio all the time and I can't find one. Does anyone know of a patch I can add to fix this?

---

### Post by FakeOutdoorsman on 2011-03-23
> **Alan James said:**
> Mono to 2 - If I don't manually up convert mono to 2 channels FFMPEG just hangs and won't do anything

I can't seem to duplicate this. Can you show your FFmpeg command and the complete output and provide an input sample if possible?

---

### Post by Alan James on 2011-03-24
The key is to use "-acodec aac -strict experimental" instead of "-ac libfaac" but here is the other information you wanted.

FFPROBE of the file

```
FFprobe version git-N-28456-g1c31b26, Copyright (c) 2007-2011 the FFmpeg developers
  built on Mar 17 2011 12:49:56 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    50. 39. 0 / 50. 39. 0
  libavcodec   52.114. 0 / 52.114. 0
  libavformat  52.103. 0 / 52.103. 0
  libavdevice  52.  3. 0 / 52.  3. 0
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '14.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 537199360
    compatible_brands: qt  
    creation_time   : 2008-02-21 22:42:25
  Duration: 00:01:43.14, start: 0.000000, bitrate: 11461 kb/s
    Stream #0.0(eng): Audio: pcm_s16be, 16000 Hz, 1 channels, s16, 256 kb/s
    Metadata:
      creation_time   : 2008-02-21 22:42:25
    Stream #0.1(eng): Video: h264 (Main), yuv420p, 640x480, 11199 kb/s, 23.98 fps, 23.98 tbr, 23976 tbn, 47952 tbc
    Metadata:
      creation_time   : 2008-02-21 22:42:25

```

FFMPEG Command

```
ffmpeg -metadata title="" -metadata artist="" -metadata copyright="" -i 14.mov \
  -vcodec libx264 -vf 'scale=640:-1' -coder 1 -flags +loop -cmp +chroma -partitions +parti8x8+parti4x4+partp8x8+partb8x8 \
  -me_method hex -subq 6 -me_range 16 -g 300 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -b_strategy 1 \
  -qcomp 0.6 -qmin 0 -qmax 69 -qdiff 4 -bf 3 -refs 2 -directpred 1 -trellis 1 \
  -flags2 +bpyramid+mixed_refs+wpred+dct8x8+fastpskip -wpredp 2 -rc_lookahead 30 -b 640k \
  -acodec aac -strict experimental -ab 96k -f mp4 -threads 0 -y 15-360.mp4
```

Output

```
FFmpeg version git-N-28456-g1c31b26, Copyright (c) 2000-2011 the FFmpeg developers
  built on Mar 17 2011 12:49:56 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    50. 39. 0 / 50. 39. 0
  libavcodec   52.114. 0 / 52.114. 0
  libavformat  52.103. 0 / 52.103. 0
  libavdevice  52.  3. 0 / 52.  3. 0
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0

Seems stream 1 codec frame rate differs from container frame rate: 47952.00 (47952/1) -> 23.98 (2997/125)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '14.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 537199360
    compatible_brands: qt  
    creation_time   : 2008-02-21 22:42:25
  Duration: 00:01:43.14, start: 0.000000, bitrate: 11461 kb/s
    Stream #0.0(eng): Audio: pcm_s16be, 16000 Hz, 1 channels, s16, 256 kb/s
    Metadata:
      creation_time   : 2008-02-21 22:42:25
    Stream #0.1(eng): Video: h264 (Main), yuv420p, 640x480, 11199 kb/s, 23.98 fps, 23.98 tbr, 23976 tbn, 47952 tbc
    Metadata:
      creation_time   : 2008-02-21 22:42:25
[buffer @ 0x1c7ff20] w:640 h:480 pixfmt:yuv420p
[scale @ 0x1ca1db0] w:640 h:480 fmt:yuv420p -> w:640 h:480 fmt:yuv420p flags:0xa0000004
[libx264 @ 0x1c656e0] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x1c656e0] profile High, level 3.0
[libx264 @ 0x1c656e0] 264 - core 114 r1913 5fd3dce - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=300 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=abr mbtree=1 bitrate=640 ratetol=1.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.41 aq=1:1.00
Output #0, mp4, to '15-360.mp4':
  Metadata:
    title           : 
    artist          : 
    copyright       : 
    major_brand     : qt  
    minor_version   : 537199360
    compatible_brands: qt  
    creation_time   : 2008-02-21 22:42:25
    encoder         : Lavf52.103.0
    Stream #0.0(eng): Video: libx264, yuv420p, 640x480, q=0-69, 640 kb/s, 2997 tbn, 23.98 tbc
    Metadata:
      creation_time   : 2008-02-21 22:42:25
    Stream #0.1(eng): Audio: libfaac, 16000 Hz, 1 channels, s16, 96 kb/s
    Metadata:
      creation_time   : 2008-02-21 22:42:25
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
```

---

### Post by FakeOutdoorsman on 2011-03-24
I still can't reproduce any hanging issues encoding from the same type of audio input with either *-acodec aac -strict experimental* or *-acodec libfaac*.

> **Alan James said:**
> 
```
ffmpeg -metadata title="" -metadata artist="" -metadata copyright="" -i 14.mov \
  -vcodec libx264 -vf 'scale=640:-1' -coder 1 -flags +loop -cmp +chroma -partitions +parti8x8+parti4x4+partp8x8+partb8x8 \
  -me_method hex -subq 6 -me_range 16 -g 300 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -b_strategy 1 \
  -qcomp 0.6 -qmin 0 -qmax 69 -qdiff 4 -bf 3 -refs 2 -directpred 1 -trellis 1 \
  -flags2 +bpyramid+mixed_refs+wpred+dct8x8+fastpskip -wpredp 2 -rc_lookahead 30 -b 640k \
  -acodec aac -strict experimental -ab 96k -f mp4 -threads 0 -y 15-360.mp4
```

Listing each option for libx264 is not recommended. Is there a particular reason that you're not using a libx264 encoding preset? According to your settings *-vpre fast* would use similar settings:
```
ffmpeg -metadata title="" -metadata artist="" -metadata copyright="" -i 14.mov \
  -vcodec libx264 -vf 'scale=640:-1' -vpre fast -b 640k \
  -acodec aac -strict experimental -ab 96k -threads 0 -y 15-360.mp4
```
I've never seen anyone apply empty metadata to the input before. Are you trying to "clear" any metadata? You can do that with '-map_metadata -1' as an output option.

Lastly, unless you're trying to target a specific output file size, then I recommend using single-pass CRF mode instead of using -b. More info: [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

---

### Post by Alan James on 2011-03-25
The presets just contain all those options anyway. I want to tweak them to individually to create the best quality to file size I can get. I wasn't able to tweak them as easily when they were inside the preset. If you can give suggestions on how to create a smaller file with great quality that would be great.

I was trying to clear the metadata and I wasn't aware of that option. I have changed it now. Thanks.

BTW I'm not as concerned with the hanging mono as I am with the incorrectly mapped 5.1.

---

### Post by FakeOutdoorsman on 2011-03-25
> **Alan James said:**
> The presets just contain all those options anyway. I want to tweak them to individually to create the best quality to file size I can get.
The presets were created so people wouldn't need to tweak the options, and if you really want to modify and options in a preset then just apply them after the preset, such as (this is just an example, I don't recommend adding *-wpredp 0* to any command):
```
-vpre slow -wpredp 0
```
Also, if you upgrade FFmpeg and x264 and the API changes then your settings could become obsolete or wrong. The presets are kept up to date with any changes.

> **Alan James said:**
> If you can give suggestions on how to create a smaller file with great quality that would be great.
The basic method is to:
[indent]1. choose the slowest preset you have patience for
2. pick the highest crf value that still gives you an acceptable quality[/indent]
If you don't care how long the encoding will take, then use *-vpre veryslow*. This preset will provide you with the higest level of compression efficiency, but, just like the name says, it's very slow. The placebo option is the slowest, but it's more of a joke than a practical preset (a ~1% improvement isn't worth the extra encoding time). Adjust the *-crf* option to change the desired quality. Increase the value until until it looks too crappy and then use the previous value. Then use this number for all encodes.

> **Alan James said:**
> BTW I'm not as concerned with the hanging mono as I am with the incorrectly mapped 5.1.
I don't think I'm going to be much help with this issue since I can't really test any output properly. You could try the [ffmpeg-user](http://ffmpeg.org/contact.html) mailing list or #ffmpeg IRC channel.

---

### Post by Alan James on 2011-03-27
Even if you don't have a 5.1 setup you can still tell that sound is coming out wrong. The sound comes mostly from the right, and very little comes from the left.

BTW I have changed my settings to use presets. I will tweak that as I go.

---

### Post by Alan James on 2011-04-02
I still haven't figured anything out about the incorrectly mapped 5.1 audio. Anyone know of any other places for me to look?

---

### Post by Alan James on 2011-04-08
bump

---

