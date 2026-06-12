---
title: "ffmpeg recording sound from program and microphone"
date: 2012-06-14
forum: Multimedia Software
---

### Post by vzybilly on 2012-06-14
I have been working all day on trying to get ffmpeg to record sound, a short list of what I've tried:
```
#Crappy screen grab
#ffmpeg -f x11grab -s "1366x768" -r "24" -i :0.0 -f mp4 ./out
#awesome screen grab, grabbing sound but non out.
#ffmpeg -f x11grab -s "1366x768" -r "24" -i :0.0 -f alsa -ac 2 -i pulse -vcodec libx264 -s "1366x768" -acodec libmp3lame -ab 128k -threads 0 -f mp4 ~/Desktop/vid
#audio test, no audio in file.
#ffmpeg -f alsa -ac 2 -i pulse -acodec libmp3lame -ab 128k -threads 0 -f mp3 ./test.mp3
#awesome screen grab.
#ffmpeg -f x11grab -s "1366x768" -r "24" -i :0.0 -threads 0 -sameq -an -f mp4 ~/Desktop/vid
```I'm running ubuntu 12.04 from beta(ish)
it would be awesome if someone could help me get this to work all in one line or (the way i'm going) multiple instances of ffmpeg (screen grab, microphone, program)

I have also tried the pavucontrol with doing the monitoring of <device> when recording audio, but that does not help either.

Thanks for all of your help, ~vzybilly~

---

### Post by sondraparkin on 2012-06-27
this is what i have found that works:
grabs the entire screen, good video quality, good audio quality (from microphone) , but you would need to edit the the args based on your hardware. 

```
ffmpeg -f alsa -ac 2 -i plughw:0,0 -f x11grab -r 100 -s 1920x1080 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 5 archinstall4.mkv
```

in ubuntu 12.04

---

### Post by vzybilly on 2012-06-27
This is what I got:

```

$ ffmpeg -f alsa -ac 2 -i plughw:0,0 -f x11grab -r 100 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 3 testVid.mkv
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[alsa @ 0x8fce240] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x8fce240] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'plughw:0,0':
  Duration: N/A, start: 433.999945, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x8fde820] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1366 height: 768
[x11grab @ 0x8fde820] shared memory extension  found
[x11grab @ 0x8fde820] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1340805516.368518, bitrate: N/A
    Stream #1.0: Video: rawvideo, bgra, 1366x768, -2147483 kb/s, 100 tbr, 1000k tbn, 100 tbc
File 'testVid.mkv' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x8fde700] w:1366 h:768 pixfmt:bgra
[avsink @ 0x8fcdf20] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x8ff3ce0] w:1366 h:768 fmt:bgra -> w:1366 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0x8fdd920] lookaheadless mb-tree requires intra refresh or infinite keyint
[libx264 @ 0x8fdd920] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x8fdd920] profile Constrained Baseline, level 4.2
[libx264 @ 0x8fdd920] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=0 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=crf mbtree=0 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=0
Output #0, matroska, to 'archinstall4.mkv':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: libx264, yuv420p, 1366x768, q=-1--1, 1k tbn, 100 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press ctrl-c to stop encoding
[alsa @ 0x8fce240] ALSA buffer xrun.
[matroska @ 0x8fcd980] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 213 >= 213
av_interleaved_write_frame(): Invalid argument

```

Any thoughts?

---

### Post by sondraparkin on 2012-06-27
1) try it with a new filename instead of changing the old filename
2) decrease the frame rate : try -r 15 instead of -r 100
see what that comes up with


for example if i was to: (with frame rate ridiculously high)
I get the same error, so you might have to play with the frame rate a little. 100 might be too high for your pc
I also get this same error by changing the frame rate on the same filname, I think it might be trying to alter the frame rate of the old instead of making a new one

```
sondra@ubuntu:~$ ffmpeg -f alsa -ac 2 -i plughw:0,0 -f x11grab -r 1000000 -s 1920x1080 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 5 archinstall4.mkv
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[alsa @ 0x18819c0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x18819c0] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'plughw:0,0':
  Duration: N/A, start: 525595.675818, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x1898ce0] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1920 height: 1080
[x11grab @ 0x1898ce0] shared memory extension  found
[x11grab @ 0x1898ce0] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1340807030.543556, bitrate: N/A
    Stream #1.0: Video: rawvideo, bgra, 1920x1080, -2147483 kb/s, 1000k tbr, 1000k tbn, 1000k tbc
File 'archinstall4.mkv' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x1883ca0] w:1920 h:1080 pixfmt:bgra
[avsink @ 0x189a9c0] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x187cf40] w:1920 h:1080 fmt:bgra -> w:1920 h:1080 fmt:yuv420p flags:0x4
[libx264 @ 0x189d700] lookaheadless mb-tree requires intra refresh or infinite keyint
[libx264 @ 0x189d700] MB rate (-429934592) > level limit (983040)
[libx264 @ 0x189d700] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2 AVX
[libx264 @ 0x189d700] profile Constrained Baseline, level 5.1
[libx264 @ 0x189d700] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=0 threads=5 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=crf mbtree=0 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=0
Output #0, matroska, to 'archinstall4.mkv':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: libx264, yuv420p, 1920x1080, q=-1--1, 1k tbn, 1000k tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press ctrl-c to stop encoding
[alsa @ 0x18819c0] ALSA buffer xrun.
[matroska @ 0x189efa0] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 210 >= 210
av_interleaved_write_frame(): Invalid argument

```

---

### Post by vzybilly on 2012-06-27
lowered it to 20 > 10 > 5.

```

$ ffmpeg -f alsa -ac 2 -i plughw:0,0 -f x11grab -r 20 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 3 testVid.mkv
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[alsa @ 0x85f9240] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x85f9240] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'plughw:0,0':
  Duration: N/A, start: 1043.999950, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x8609820] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1366 height: 768
[x11grab @ 0x8609820] shared memory extension  found
[x11grab @ 0x8609820] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1340816121.816565, bitrate: 671416 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1366x768, 671416 kb/s, 20 tbr, 1000k tbn, 20 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x8609700] w:1366 h:768 pixfmt:bgra
[avsink @ 0x85f8f20] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x861ece0] w:1366 h:768 fmt:bgra -> w:1366 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0x8608920] lookaheadless mb-tree requires intra refresh or infinite keyint
[libx264 @ 0x8608920] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x8608920] profile Constrained Baseline, level 3.2
[libx264 @ 0x8608920] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=0 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=20 scenecut=0 intra_refresh=0 rc=crf mbtree=0 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=0
Output #0, matroska, to 'testVid.mkv':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: libx264, yuv420p, 1366x768, q=-1--1, 1k tbn, 20 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press ctrl-c to stop encoding
[alsa @ 0x85f9240] ALSA buffer xrun.
[matroska @ 0x85f8980] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 262 >= 262
av_interleaved_write_frame(): Invalid argument
vzybilly@vzyLappy-i3:~$ ffmpeg -f alsa -ac 2 -i plughw:0,0 -f x11grab -r 10 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 3 testVid2.mkv
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[alsa @ 0x9267240] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x9267240] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'plughw:0,0':
  Duration: N/A, start: 1117.999984, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x9277820] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1366 height: 768
[x11grab @ 0x9277820] shared memory extension  found
[x11grab @ 0x9277820] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1340816196.139167, bitrate: 335708 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1366x768, 335708 kb/s, 10 tbr, 1000k tbn, 10 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x9277700] w:1366 h:768 pixfmt:bgra
[avsink @ 0x9266f20] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x928cce0] w:1366 h:768 fmt:bgra -> w:1366 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0x9276920] lookaheadless mb-tree requires intra refresh or infinite keyint
[libx264 @ 0x9276920] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x9276920] profile Constrained Baseline, level 3.2
[libx264 @ 0x9276920] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=0 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=10 scenecut=0 intra_refresh=0 rc=crf mbtree=0 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=0
Output #0, matroska, to 'testVid2.mkv':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: libx264, yuv420p, 1366x768, q=-1--1, 1k tbn, 10 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press ctrl-c to stop encoding
[alsa @ 0x9267240] ALSA buffer xrun.
[matroska @ 0x9266980] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 2083 >= 2083
av_interleaved_write_frame(): Invalid argument
vzybilly@vzyLappy-i3:~$ ffmpeg -f alsa -ac 2 -i plughw:0,0 -f x11grab -r 5 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 3 testVid3.mkv
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[alsa @ 0x8c5c240] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x8c5c240] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'plughw:0,0':
  Duration: N/A, start: 1151.999955, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x8c6c820] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1366 height: 768
[x11grab @ 0x8c6c820] shared memory extension  found
[x11grab @ 0x8c6c820] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1340816230.265946, bitrate: 167854 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1366x768, 167854 kb/s, 5 tbr, 1000k tbn, 5 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x8c6c700] w:1366 h:768 pixfmt:bgra
[avsink @ 0x8c5bf20] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x8c81ce0] w:1366 h:768 fmt:bgra -> w:1366 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0x8c6b920] lookaheadless mb-tree requires intra refresh or infinite keyint
[libx264 @ 0x8c6b920] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x8c6b920] profile Constrained Baseline, level 3.2
[libx264 @ 0x8c6b920] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=0 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=5 scenecut=0 intra_refresh=0 rc=crf mbtree=0 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=0
Output #0, matroska, to 'testVid3.mkv':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: libx264, yuv420p, 1366x768, q=-1--1, 1k tbn, 5 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press ctrl-c to stop encoding
[alsa @ 0x8c5c240] ALSA buffer xrun.  1kB time=10000000000.00 bitrate=   0.0kbits/s    
[matroska @ 0x8c5b980] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 584 >= 584
av_interleaved_write_frame(): Invalid argument

```Thank you for your help~

---

### Post by mwclark4453 on 2012-06-27
Worked for me as well, thanks.

---

### Post by vzybilly on 2012-06-27
it's still giving me errors...

Could you get it not to do the video?
I'll work on it myself and see if I can get it to work without the video part...

EDIT:
I got it to record the sound with ```
ffmpeg -f alsa -ac 2 -i plughw:0,0 test.mp3
``` Now to work on both?

---

### Post by vzybilly on 2012-06-27
I have gotten it to work, I have made a small script that will record both audio and video
Here is my script:

```
#!/bin/bash
#vzybilly
#these are temp files
aud="aud.mp3"
vid="vid.mp4"
#grab audio & pid
ffmpeg -f alsa -ac 2 -i plughw:0,0 $aud &
audPID=$!
#grab screen & pid
ffmpeg -f x11grab -s "1366x768" -r "24" -i :0.0 -threads 0 -sameq -an -f mp4 $vid &
vidPID=$!
#wait, till name given (that means stop)
read -p "Stop by giving an Output video name?" out
#stop audio and video with pids
kill -n 2 $audPID
kill -n 2 $vidPID
echo "Saving to $out"
#combine to the target output file
ffmpeg -i $aud -i $vid -acodec copy -vcodec copy "$out"
#purge the temp files
rm $aud
rm $vid
```Only issue so far, the recording ffmpegs output and make it hard to tell the name for the output video when typing, anyone know a stop for that?

Thank you for all of your help
~vzybilly~

---

### Post by shantiq on 2012-06-27
you might like a more [**simple**]("http://ubuntuforums.org/showthread.php?t=1805550") approach which requires simpler commands

---

### Post by vzybilly on 2012-06-27
> **shantiq said:**
> you might like a more [**simple**]("http://ubuntuforums.org/showthread.php?t=1805550") approach which requires simpler commands
I've tried working with pavucontrol and I got no audio in my audio files, I got this all working good now so I'm happy...

---

### Post by la1234uk on 2012-09-20
This method is pretty straighforward and works with my 12.04:

ffmpeg -f alsa -i pulse -acodec pcm_s16le output.aif

Cheers,

GR

---

