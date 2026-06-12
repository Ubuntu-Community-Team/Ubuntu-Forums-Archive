---
title: "ffmpeg: Bad performance on capturing"
date: 2011-10-25
forum: Multimedia Software
---

### Post by Sworddragon on 2011-10-25
I want to capture some things with ffmpeg but the performance is bad. For example:

```
ffmpeg -f alsa -i hw:0,0 -f x11grab -r 30 -s 1680x1050 -i :0.0 -sameq -vcodec mpeg4 /tmp/ffmpeg/test.mkv
```

The FPS are only ~15. ffmpeg uses for one of my 2 cores ~85% and X ~12%. If I add -threads 2 the cpu usage increases on ffmpeg to ~99% of one core and on X to ~15%. The FPS are increasing to 17 too. Here is the output of such a run:

```
sworddragon@ubuntu:~$ ffmpeg -f alsa -i hw:0,0 -f x11grab -r 30 -s 1680x1050 -i :0.0 -sameq -threads 2 -vcodec mpeg4 /tmp/ffmpeg/test.mkv
ffmpeg version 0.7.2-4:0.7.2-1ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Oct  2 2011 15:13:26 with gcc 4.6.1
  configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  5. 0 / 53.  5. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[color=#AA5500][alsa @ 0x15cc340] Estimating duration from bitrate, this may be inaccurate[/color]
Input #0, alsa, from 'hw:0,0':
  Duration: N/A, start: 154223.326013, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x15df100] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1680 height: 1050
[x11grab @ 0x15df100] shared memory extension  found
[color=#AA5500][x11grab @ 0x15df100] Estimating duration from bitrate, this may be inaccurate[/color]
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1319565906.132963, bitrate: 1693440 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1680x1050, 1693440 kb/s, 30 tbr, 1000k tbn, 30 tbc
File '/tmp/ffmpeg/test.mkv' already exists. Overwrite ? [y/N] y
[color=#AA5500]Incompatible pixel format 'bgra' for codec 'mpeg4', auto-selecting format 'yuv420p'[/color]
[buffer @ 0x15def80] w:1680 h:1050 pixfmt:bgra
[ffsink @ 0x15cc260] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x15ec880] w:1680 h:1050 fmt:bgra -> w:1680 h:1050 fmt:yuv420p flags:0x4
Output #0, matroska, to '/tmp/ffmpeg/test.mkv':
  Metadata:
    encoder         : Lavf53.2.0
    Stream #0.0: Video: mpeg4, yuv420p, 1680x1050, q=2-31, 200 kb/s, 1k tbn, 30 tbc
    Stream #0.1: Audio: mp2, 48000 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press ctrl-c to stop encoding
[color=#AA5500][alsa @ 0x15cc340] ALSA buffer xrun.[/color]
^Cframe=  179 fps= 17 q=0.0 Lsize=    4151kB time=10.49 bitrate=3242.0kbits/s    
video:4063kB audio:82kB global headers:0kB muxing overhead 0.127000%
Received signal 2: terminating.
```

If I change -vcodec to the lossless ffv1 the FPS are decreasing to 10. Another problem is that the captured sound is very bad. I tried some lossless audio codecs but I got every time an error about an unsupported sample format. For example -acodec flac gives me:

```
[color=#FF5555][alsa @ 0x14ad360] sample format 0x1500e is not supported[/color]
```

My CPU is an AMD Athlon X2 3800+ @ 2GHz. Is there any configuration that allows me to get 30 FPS on this resolution? I'm wondering why ffmpeg isn't using the full core on 1 thread because it hasn't reached 30 FPS. The second thread doesn't use another core too. I think this is a bug and I will open a ticket for this. Another question is how I can get a lossless audio configuration with ffmpeg.

---

### Post by FakeOutdoorsman on 2011-10-25
The hard part is figuring out what the bottleneck is: x11grab, ffmpeg, encoder, your options, CPU, hard drive, or other. First compile FFmpeg. There are some recent changes that make capturing with libx264 somewhat faster that are probably missing from the repository version (by the way the repo version is from libav, not FFmpeg).

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Now try a simpler command. This example will deal just with video and will output as "null" which avoids creating an output file so you can cut out some potential bottlenecks. It will also use the libx264 encoder which should be faster than the encoder called mpeg4.
```
ffmpeg -f x11grab -r 30 -s 1680x1050 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -f null -y /dev/null
```
Does the fps number at the bottom of the console output show that you are encoding at 30 fps?

If yes, then continue with [HOWTO: Proper Screencasting on Linux](ubuntuforums.org/showthread.php?p=8746719#post8746719)

---

### Post by Sworddragon on 2011-10-26
I get 30 FPS and followed the screencasting guide. But ffmpeg is aborting with an error:

```
sworddragon@ubuntu:~$ ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s 1680x1050+0+0 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 /tmp/ffmpeg/test.mkv
ffmpeg version git-2011-10-26-4416931, Copyright (c) 2000-2011 the FFmpeg developers
  built on Oct 26 2011 19:38:28 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab
  libavutil    51. 22. 0 / 51. 22. 0
  libavcodec   53. 23. 0 / 53. 23. 0
  libavformat  53. 17. 0 / 53. 17. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 45. 0 /  2. 45. 0
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[color=#AA5500][alsa @ 0x30088a0] Estimating duration from bitrate, this may be inaccurate[/color]
Input #0, alsa, from 'hw:0,0':
  Duration: N/A, start: 1319654593.671758, bitrate: N/A
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x3003080] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1680 height: 1050
[x11grab @ 0x3003080] shared memory extension found
[color=#AA5500][x11grab @ 0x3003080] Estimating duration from bitrate, this may be inaccurate[/color]
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1319654593.710245, bitrate: 1693440 kb/s
    Stream #1:0: Video: rawvideo (BGRA / 0x41524742), bgra, 1680x1050, 1693440 kb/s, 30 tbr, 1000k tbn, 30 tbc
[color=#AA5500]Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'[/color]
[buffer @ 0x3008620] w:1680 h:1050 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0x3006b80] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 0x300a540] w:1680 h:1050 fmt:bgra -> w:1680 h:1050 fmt:yuv420p flags:0x4
[libx264 @ 0x3007580] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0x3007580] profile High 4:4:4 Predictive, level 4.0, 4:2:0 8-bit
[libx264 @ 0x3007580] 64 - core 119 r2106 07efeb4 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to '/tmp/ffmpeg/test.mkv':
  Metadata:
    encoder         : Lavf53.17.0
    Stream #0:0: Video: h264, yuv420p, 1680x1050, q=-1--1, 1k tbn, 30 tbc
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #1.0 -> #0.0 (rawvideo -> libx264)
  Stream #0.0 -> #0.1 (pcm_s16le -> pcm_s16le)
Press [q] to stop, [?] for help
[color=#AA5500][alsa @ 0x30088a0] ALSA buffer xrun.[/color]
[color=#FF5555][matroska @ 0x3006c40] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 47 >= 47
av_interleaved_write_frame(): Invalid argument[/color]
```


Edit: I have made some tests and it is working now with this command:

```
ffmpeg -f alsa -acodec pcm_s16le -i hw:0,0 -f x11grab -r 30 -s 1680x1050+0+0 -i :0.0 -vcodec libx264 -threads 0 /tmp/ffmpeg/test.mkv
```

The FPS are ~20 but dropping to ~15 if an "ALSA buffer xrun." appears. The the format is converted to yuv420p because bgra is not known for libx264. Trying to use rgb24 will give me wrong colors. What is this "ALSA buffer xrun." and how can I use a lossless pixel format for libx264?

---

### Post by FakeOutdoorsman on 2011-10-26
> **Sworddragon said:**
> I get 30 FPS and followed the screencasting guide. But ffmpeg is aborting with an error:

```
[color=#AA5500][alsa @ 0x30088a0] ALSA buffer xrun.[/color]
[color=#FF5555][matroska @ 0x3006c40] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 47 >= 47
av_interleaved_write_frame(): Invalid argument[/color]
```
I also encounter this error. I was preparing a bug report about it a few weeks ago but got sidetracked. It only occurred with pcm audio in matroska container if I remember correctly. I'll take another look soon.

> **Sworddragon said:**
> Edit: I have made some tests and it is working now with this command:
```
ffmpeg -f alsa -acodec pcm_s16le -i hw:0,0 -f x11grab -r 30 -s 1680x1050+0+0 -i :0.0 -vcodec libx264 -threads 0 /tmp/ffmpeg/test.mkv
```
Interesting that adding *-acodec pcm_s16le* allowed it to work for you especially since FFmpeg initially views the input as pcm_s16le.

> **Sworddragon said:**
> The FPS are ~20 but dropping to ~15 if an "ALSA buffer xrun." appears.
I'm not sure what to recommend for this yet. I know little about ALSA.

> **Sworddragon said:**
> The the format is converted to yuv420p because bgra is not known for libx264. Trying to use rgb24 will give me wrong colors...and how can I use a lossless pixel format for libx264?
libx264 seems to accept *-pix_fmt bgr24* with x11grab, although I'm unsure if that is a correct or sane choice. However, upon playback:
```
$ ffplay output.mkv 
ffplay version N-34065-g742d218, Copyright (c) 2003-2011 the FFmpeg developers
  built on Oct 26 2011 14:42:13 with gcc 4.6.1 20110819 (prerelease)
  configuration: --prefix=/usr --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil    51. 22. 0 / 51. 22. 0
  libavcodec   53. 23. 0 / 53. 23. 0
  libavformat  53. 17. 0 / 53. 17. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 45. 0 /  2. 45. 0
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, matroska,webm, from 'output.mkv':
  Metadata:
    ENCODER         : Lavf53.17.0
  Duration: 00:00:05.03, start: 0.000000, bitrate: 3063 kb/s
    Stream #0:0: Video: h264 (High 4:4:4 Predictive), gbr24p, 1680x1050, SAR 1:1 DAR 8:5, 30 fps, 30 tbr, 1k tbn, 60 tbc (default)
[buffersink @ 0x26ebcc0] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
**[scale @ 0x26beca0] w:1680 h:1050 fmt:gbr24p -> w:1680 h:1050 fmt:yuv420p flags:0x4**
```

---

### Post by FakeOutdoorsman on 2011-10-27
> **FakeOutdoorsman said:**
> Interesting that adding *-acodec pcm_s16le* allowed it to work for you especially since FFmpeg initially views the input as pcm_s16le.
Duh...now I know one reason why it could be working. FFmpeg is not using pcm_s16le for the output, but something else like libvorbis which does not cause this issue.

---

### Post by Sworddragon on 2011-10-28
> **FakeOutdoorsman said:**
> libx264 seems to accept *-pix_fmt bgr24* with x11grab, although I'm unsure if that is a correct or sane choice.

I get the same result as rgb24. For example the black background from the terminal is green in the video.


> **FakeOutdoorsman said:**
> Duh...now I know one reason why it could be working. FFmpeg is not using pcm_s16le for the output, but something else like libvorbis which does not cause this issue.

It seems -acodec pcm_s16le was at the wrong place in my command and was ignored then (libvorbis is used as default then). I have now used -acodec vorbis at the correct position but ffmpeg is saying that I need to use -strict experimental with libvorbis (curious that the implicit using of libvorbis isn't complaining about -strict experimental).

---

### Post by hugmenot on 2011-10-29
> **Sworddragon said:**
> I get the same result as rgb24. For example the black background from the terminal is green in the video.


try -profile high444

---

### Post by Sworddragon on 2011-10-30
> **hugmenot said:**
> try -profile high444

```
ffmpeg version git-2011-10-30-3c32a94, Copyright (c) 2000-2011 the FFmpeg developers
  built on Oct 30 2011 11:23:59 with gcc 4.6.2
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab
  libavutil    51. 22. 0 / 51. 22. 0
  libavcodec   53. 25. 0 / 53. 25. 0
  libavformat  53. 18. 0 / 53. 18. 0
sworddragon@ubuntu:~/data/Scripte/python$   libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 45. 1 /  2. 45. 1
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[color=#AA5500][alsa @ 0x1f147c0] Estimating duration from bitrate, this may be inaccurate[/color]
Input #0, alsa, from 'hw:0,0':
  Duration: N/A, start: 1319971074.563833, bitrate: N/A
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x1f0f080] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1680 height: 1050
[x11grab @ 0x1f0f080] shared memory extension found
[color=#AA5500][x11grab @ 0x1f0f080] Estimating duration from bitrate, this may be inaccurate[/color]
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1319971074.606299, bitrate: 1693440 kb/s
    Stream #1:0: Video: rawvideo (BGRA / 0x41524742), bgra, 1680x1050, 1693440 kb/s, 30 tbr, 1000k tbn, 30 tbc
[buffer @ 0x1f12d20] w:1680 h:1050 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0x1f12a80] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 0x1f16100] w:1680 h:1050 fmt:bgra -> w:1680 h:1050 fmt:rgb24 flags:0x4
[libx264 @ 0x1f13720] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0x1f13720] profile High 4:4:4 Predictive, level 4.0, 4:4:4 8-bit
[libx264 @ 0x1f13720] 264 - core 119 r2106 07efeb4 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=0 threads=2 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=crf mbtree=0 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=0
[color=#FF5555][NULL @ 0x1f14120] [Eval @ 0x7fffc1c06730] Undefined constant or missing '(' in 'high444'
[NULL @ 0x1f14120] Unable to parse option value "high444"
[NULL @ 0x1f14120] Error setting option profile to value high444.[/color]
Output #0, matroska, to '/tmp/ffmpeg/2011_10_30_11_37_54-1.mkv':
    Stream #0:0: Video: h264, rgb24, 1680x1050, q=-1--1, 90k tbn, 30 tbc
    Stream #0:1: Audio: none, 48000 Hz, 2 channels, s16, 128 kb/s
Stream mapping:
  Stream #1.0 -> #0.0 (rawvideo -> libx264)
  Stream #0.0 -> #0.1 (pcm_s16le -> flac)
[color=#FF5555]Error while opening encoder for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height[/color]
```

Where must the argument be placed? I have placed it after -preset ultrafast. I have tested now -acodec flac and got 5 FPS more (20). With -pix_fmt rgb24 I'm getting even 30 FPS but I must first find a solution for the wrong colors.

---

### Post by hugmenot on 2011-10-30
That looks very strange. Seems ffmpeg is somehow broken.

This line tells that at least x264 recognizes 4:4:4 color sampling, which you need for rgb or bgr24, i.e. 3×8-bit color channels.

[libx264 @ 0x1f13720] profile High 4:4:4 Predictive, level 4.0, 4:4:4 8-bit

---

### Post by hugmenot on 2011-10-30
Can’t you also try to record in flashsv, which is a fast ScreenVideo codec and pretty much lossles and then exncode to x264 post-hoc?

---

### Post by FakeOutdoorsman on 2011-10-30
> **hugmenot said:**
> That looks very strange. Seems ffmpeg is somehow broken.
It's an annoying quirk that *-vprofile* should be used instead of *-profile* when audio is also being encoded.

---

### Post by Sworddragon on 2011-10-30
With -vprofile it is working and I get in a line:

```
[libx264 @ 0x2ae9720] profile High 4:4:4 Predictive, level 4.0, 4:4:4 8-bit
```

But the colors are still wrong with rgb24 and bgr24.

---

### Post by hugmenot on 2011-10-31
> **Sworddragon said:**
> With -vprofile it is working and I get in a line:

```
[libx264 @ 0x2ae9720] profile High 4:4:4 Predictive, level 4.0, 4:4:4 8-bit
```

But the colors are still wrong with rgb24 and bgr24.

Ok, my idea was misguided. See here: [http://doom10.org/index.php?topic=152.0](http://doom10.org/index.php?topic=152.0)

---

### Post by Sworddragon on 2011-10-31
> **hugmenot said:**
> Ok, my idea was misguided. See here: [http://doom10.org/index.php?topic=152.0](http://doom10.org/index.php?topic=152.0)

The thread says that h.264 doesn't support RGB. If this is true x264 doesn't support a real lossless mode. I wanted to try libvpx some days ago but found no way for a lossless mode (I found on Google that libvpx doesn't support a lossless mode). Is there any codec which has a **real** lossless mode with a good speed?

---

