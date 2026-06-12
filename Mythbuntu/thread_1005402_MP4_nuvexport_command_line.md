---
title: "MP4 nuvexport command line"
date: 2008-12-08
forum: Mythbuntu
---

### Post by johnelle on 2008-12-08
I am having trouble crafting the correct **nuvexport** command line for MP4 transcoding.  I have it MP4 working fine in interactive (terminal) mode but it dies as a transcode and I don't see any abnormal messages in the log.  Any ideas?

The command line:

```
nuvexport --mode ipod --input="%FILE%"
```

When the job runs in the log:

```
2008-12-08 07:38:32.379 JobQueue: Started "Convert to MPEG4" for "Guthy-Renker" recorded from channel 1008 at Mon Dec 8 07:12:00 2008
'unknown': unknown terminal type.
2008-12-08 07:38:32.961 MainServer::HandleAnnounce Monitor
2008-12-08 07:38:32.966 adding: mythbuntu as a client (events: 0)
Loading MythTV recording info.
80% 
h.264 mp4/ipod encoding requires the svn version of ffmpeg.

Cleaning up temp files.
2008-12-08 07:38:33.893 JobQueue: Finished "Convert to MPEG4" for "Guthy-Renker" recorded from channel 1008 at Mon Dec 8 07:12:00 2008.
2008-12-08 07:43:27.412 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

There is no file output from this--it ends almost immediately.

John

---

### Post by SiHa on 2008-12-08
When running in interactive mode, what transcoder did you pick (transcode, mencoder, ffmpeg)? Judging by the error, it's unlikely it was ffmpeg.
Your command line doesn't specify which one to use, so it will use the default specified in **/etc/nuvexprtrc**, which I guess is ffmpeg.
FWIW, I find that transcode gives me the best results - I convert to Xvid .AVI

---

### Post by rhpot1991 on 2008-12-08
If you are looking for support for iPod or other portable devices you may want to poke at MytheExport:

[https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

---

### Post by johnelle on 2008-12-08
Yes the rc file points to ffmpeg and in interactive mode I select "ipod" which is menu item "10" on my machine.  The ffmpeg came from the "restricted" package because a couple of quick attempts at building it from source made me think it was going to be tedious.

The weird thing is that I am not getting anything unusual in the log.  It just dies silently.

John

---

### Post by Stradenko on 2009-05-16
I'm getting this same (and another) error in Jaunty.
command-line, I get this:
```
$ /usr/bin/nuvexport --input /myth/tv/1054_20090512212900.nuv --mode mp4 --path=/tmp
Loading MythTV recording info.
99% 
h.264 mp4/ipod encoding requires the svn version of ffmpeg.

Cleaning up temp files.

```interactively, I get this:
```
$ nuvexport --ffmpeg

*selected  10. Export to MP4 (iPod)*

Choose a function, or episode(s) to remove:  c
Where would you like to export the files to? [.] 
Enable Myth cutlist? [Yes] 
Enable noise reduction (slower, but better results)? [No] 
Enable deinterlacing? [Yes] 
Crop broadcast overscan border (0-5%) ? [1.5] 
Audio bitrate? [64] 
Enable iPod compatibility? [Yes] 
Using the mpeg4 codec (h.264 mp4/ipod encoding requires the svn version of ffmpeg.)
Variable bitrate video? [Yes] 
Multi-pass (slower, but better quality)? [Yes] 
Video bitrate? [384] 
Default resolution based on requested dimensions.
Width? [320] 
Height? [240] 

Now encoding:  Show name
Encode started:  Sat May 16 06:31:22 2009
First pass...
Waiting for mythtranscode to set up the fifos.
Starting ffmpeg.
Use of uninitialized value in numeric gt (>) at /usr/share/nuvexport/export/ffmpeg.pm line 378, <STDIN> line 16.
processed:  0 of 0 frames at 0 fps (~%, eta: unknown)  

ffmpeg had critical errors:

ffmpeg: unrecognized option '-title'

Cleaning up temp files.
Cleaning up child processes.

```ffmpeg version:```

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
FFmpeg 0.5-svn17737+3:0.svn20090303-1ubuntu6
libavutil     49.15. 0 / 49.15. 0
libavcodec    52.20. 0 / 52.20. 0
libavformat   52.31. 0 / 52.31. 0
libavdevice   52. 1. 0 / 52. 1. 0
libavfilter    0. 4. 0 /  0. 4. 0
libswscale     0. 7. 1 /  0. 7. 1
libpostproc   51. 2. 0 / 51. 2. 0

```I have the appropriate packages to encode using libfaac:
```
$ ffmpeg -formats 2>/dev/null |grep aac
 D  aac             raw ADTS AAC
 D A    aac             Advanced Audio Coding
  EA    libfaac         libfaac AAC (Advanced Audio Codec)

```

Thoughts?  Was the issue ever resolved for the original poster?

---

