---
title: "question about FFmpeg and recent changes"
date: 2012-06-23
forum: Multimedia Software
---

### Post by shantiq on 2012-06-23
this here    to grab desktop and microphone no longer works 
i know the syntax has shifted but do not know how to rectify this







> ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 ./Desktop/mydesktop.mkv



now gives me

> ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 ./Desktop/mydesktop.mkv
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[alsa @ 0x20dd9a0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x20dd9a0] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1340438436.271292, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x20de700] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1024 height: 768
[x11grab @ 0x20de700] shared memory extension  found
[x11grab @ 0x20de700] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1340438436.346524, bitrate: 754974 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1024x768, 754974 kb/s, 30 tbr, 1000k tbn, 30 tbc
File './Desktop/mydesktop.mkv' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x2101100] w:1024 h:768 pixfmt:bgra
[avsink @ 0x2104380] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x2104a60] w:1024 h:768 fmt:bgra -> w:1024 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0x21033a0] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0x21033a0] profile High 4:4:4 Predictive, level 3.1, 4:2:0 8-bit
[libx264 @ 0x21033a0] 64 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - [http://www.videolan.org/x264.html](http://www.videolan.org/x264.html) - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to './Desktop/mydesktop.mkv':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: libx264, yuv420p, 1024x768, q=-1--1, 1k tbn, 30 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press ctrl-c to stop encoding
[B][COLOR="DarkRed"][matroska @ 0x2101780] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1 >= 1
av_interleaved_write_frame(): Invalid argument[/COLOR][/B]
shantiq@shantiq-00000000000000000000000:~$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 ./Desktop/mydesktop.mkv




i have been able to use this instead

> ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1600x900 -i :0.0 -acodec flac  -vcodec libx264 -y  -threads 0 ./Desktop/mydesktop.mkv


but of course lose the lossless on the image

so my question is how to adapt the top line to make it work with 12.04


my version is this

> ffmpeg
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3


---

### Post by shantiq on 2012-06-24
any of you learned chaps?:KS would love to get this working again:KS

---

### Post by mc4man on 2012-06-24
Haven't spent much time with as of late for various reasons so can't exactly fix your command

I's suggest that on 12.04/12.10 you either use  avconv or build yourself the current real FFmpeg if you want to use ffmpeg command

Actually got a bit interested today in creating a unity launcher for FFmpeg &  x11grab so obviously needed a basic command that worked. While likely avconv & ffmpeg are similar/the same here I gave up reading man avconv, built the latest FFmpeg & created a nicely working launcher 

You can find some clues here, ck. post 2164 
[http://ubuntuforums.org/showthread.php?t=786095&page=109](http://ubuntuforums.org/showthread.php?t=786095&page=109)

( what I ended up with auto names the capture based on date + time & works well from the unity launcher or Dash, shown in both in screenshot.
I used a basic command for the script that does a good job though not lossless, couldn't find enough info otherwise, so will ck. back here to see if someone gives you a nice one

If interested in the launcher let me know

---

### Post by FakeOutdoorsman on 2012-06-25
Try this. It will make video and audio outputs to separate files that you can then combine.

```
avconv -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -vcodec libx264 -vpre lossless_ultrafast -threads 0 -an video.mkv -acodec copy audio.wav
ffmpeg -i video.mkv -i audio.wav -vcodec copy -acodec copy output.mkv

```

I'm only use ffmpeg from FFmpeg the project, so I'm not sure what will work with avconv.

Syntax for real ffmpeg:
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -an video.mkv -acodec copy audio.wav
ffmpeg -i video.mkv -i audio.wav -c copy output.mkv

```

Switch *-acodec copy* with *-acodec pcm_s16le* if it gives you issues.

---

### Post by shantiq on 2012-06-25
thanx guys but still moaning:KS

> shantiq@shantiq-00000000000000000000000:~$ avconv -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -vcodec libx264 -vpre lossless_ultrafast -threads 0 -an video.mkv -acodec copy audio.wav
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
[alsa @ 0xe01aa0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0xe01aa0] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1340618247.285518, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0xe227a0] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1024 height: 768
[x11grab @ 0xe227a0] shared memory extension  found
[x11grab @ 0xe227a0] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1340618247.338623, bitrate: 754974 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1024x768, 754974 kb/s, 30 tbr, 1000k tbn, 30 tbc
[B]Unrecognized option 'vpre'
Failed to set value 'lossless_ultrafast' for option 'vpre'[/B]



aaarrghh

---

### Post by mc4man on 2012-06-25
For avconv in 12.04 I think I'd try -pre instead of -vpre .Other than that you'd have to see & work out as you go as I won't install libav-tools anymore on this install (12.10

---

### Post by shantiq on 2012-06-25
thanx for checking Mc4   but  as yet not

let me clarify

more than happy for sound to remain at flac level   i do not need wav    but what i have lost here is the lossless image which was so sharp with old command

> ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -[COLOR="Red"]vcodec libx264 -vpre lossless_ultrafast -threads 0[/COLOR]  ./Desktop/mydesktop.mkv
   i think the highlighted in red section is where the problem now is 

    this was in my [**grab desktop guide**]("http://ubuntuforums.org/showthread.php?t=1710642") but for me on 12.04 at the moment  no longer a starter


> shantiq@shantiq-00000000000000000000000:~$ avconv -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -vcodec libx264 -pre lossless_ultrafast -threads 0 -an video.mkv -acodec copy audio.wav
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
[alsa @ 0x10cdaa0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x10cdaa0] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1340635207.131411, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x10ce7e0] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1024 height: 768
[x11grab @ 0x10ce7e0] shared memory extension  found
[x11grab @ 0x10ce7e0] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1340635207.192724, bitrate: 754974 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1024x768, 754974 kb/s, 30 tbr, 1000k tbn, 30 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x10f8000] w:1024 h:768 pixfmt:bgra
[avsink @ 0x10f6f00] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x10f2b20] w:1024 h:768 fmt:bgra -> w:1024 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0x10f6900] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0x10f6900] profile High 4:4:4 Predictive, level 3.1, 4:2:0 8-bit
[libx264 @ 0x10f6900] 64 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - [http://www.videolan.org/x264.html](http://www.videolan.org/x264.html) - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'video.mkv':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: libx264, yuv420p, 1024x768, q=-1--1, 1k tbn, 30 tbc
Output #1, wav, to 'audio.wav':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #1.0: Audio: pcm_s16le, 48000 Hz, 2 channels, 1536 kb/s
Stream mapping:
  Stream #1:0 -> #0:0 (rawvideo -> libx264)
  Stream #0:0 -> #1:0 (copy)
Press ctrl-c to stop encoding
[COLOR="Red"][wav @ 0x10efe80] Application provided invalid, non monotonically increasing dts to muxer in stream 0: 1578 >= 1552
av_interleaved_write_frame(): Invalid argument[/COLOR]


---

### Post by mc4man on 2012-06-25
Well - avconv seems to act wierdly with the command you are using ??
Running that exact command on 12.04 - 
sometimes it ends with
> Press ctrl-c to stop encoding
[wav @ 0xc71760] Application provided invalid, non monotonically increasing dts to muxer in stream 0: 270586 >= 270581
av_interleaved_write_frame(): Invalid argument

Other times it proceeds fine

To show, clipping unneeded
> 
$ avconv -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -vcodec libx264 -pre lossless_ultrafast -threads 0 -an video.mkv -acodec copy audio.wav
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
...clipped
Stream mapping:
  Stream #1:0 -> #0:0 (rawvideo -> libx264)
  Stream #0:0 -> #1:0 (copy)
Press ctrl-c to stop encoding
[wav @ 0xc71760] Application provided invalid, non monotonically increasing dts to muxer in stream 0: 270586 >= 270581
av_interleaved_write_frame(): Invalid argument

~$ avconv -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -vcodec libx264 -pre lossless_ultrafast -threads 0 -an video.mkv -acodec copy audio.wav
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
....clipped
Stream mapping:
  Stream #1:0 -> #0:0 (rawvideo -> libx264)
  Stream #0:0 -> #1:0 (copy)
Press ctrl-c to stop encoding
^Cframe=   94 fps= 30 q=-1.0 Lsize=     621kB time=6.00 bitrate= 847.6kbits/s dup=0 drop=19    
video:620kB audio:0kB global headers:0kB muxing overhead 0.184079%
...ect.
I'd get rid of libav-tools, build FFmpeg & use previous FFmpeg commands posted
Otherwise just keep repeating till it works... or alter the audio command??

---

