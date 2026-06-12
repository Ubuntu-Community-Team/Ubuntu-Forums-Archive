---
title: "ffmpeg and dual core."
date: 2010-02-09
forum: Multimedia Software
---

### Post by markp1989 on 2010-02-09
im converting alot of my tv shows for use on ipods. 

i wrote a small bash script that i can run on eash season i like.

```

for file in *.avi
do
ffmpeg -y -i "$file" -threads 2 -s 320x180 -vcodec mpeg4  -ab 128k -acodec libfaac -ac 2 -ab 64k -f mp4 "ipod/$file.mp4"
done
```

i have set threads to 2, but it still only uses one core. 

so i started thinking , that i could alter the script to cue up the files to run 2 at a time, but i dont know how, any help will be appriiated.

thanks markp1989

---

### Post by FakeOutdoorsman on 2010-02-10
You can probably get better results with libx264 which will create H.264 video and will automatically detect a proper threads value.  Here's an example using the ipod320 preset:
```
ffmpeg -i input -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -vpre ipod320 -crf 26 -threads 0 -f ipod -metdata title="A History of Ham" output.mp4
```
I must admit that I don't own an iPod to test this command, but I have no reason to doubt the effectiveness of it.

I recommend compiling x264 and FFmpeg if you're going to convert more than a few videos.  Development is active and compiling gives you the most recent version so you can make sure you're not missing any exciting new features:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by markp1989 on 2010-02-10
> **FakeOutdoorsman said:**
> You can probably get better results with libx264 which will create H.264 video and will automatically detect a proper threads value.  Here's an example using the ipod320 preset:
```
ffmpeg -i input -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -vpre ipod320 -crf 26 -threads 0 -f ipod -metdata title="A History of Ham" output.mp4
```
I must admit that I don't own an iPod to test this command, but I have no reason to doubt the effectiveness of it.

I recommend compiling x264 and FFmpeg if you're going to convert more than a few videos.  Development is active and compiling gives you the most recent version so you can make sure you're not missing any exciting new features:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

thats slower then what i was using before it only used 40% of 1 core.

i have been looking for a way to have the script break the list in half and then run 2 instances of ffmpeg (right now the 1 instance i have uses about 95% of 1 core)

any tips will be appriciated, thanks :)

edit: so far i have it running like this to use both cores (im sure there is a better way to do it ) 

```

#!/bin/bash
mkdir ipod 

(for file in $(ls *.avi)
do
if [ -f "ipod/$file.m4a" ]
  then
    echo "file already exists: ipod/$file.m4a"
  else
    ffmpeg -y -i "$file" -s 320x180 -vcodec mpeg4 -ab 128k -acodec libfaac -ac 2 -ab 64k -f mp4 "ipod/$file.m4a"
fi
done) &

(for file in $(ls *.avi | sort -r)
do
if [ -f "ipod/$file.m4a" ]
  then
    echo "file already exists: ipod/$file.m4a"
  else
    ffmpeg -y -i "$file" -s 320x180 -vcodec mpeg4 -ab 128k -acodec libfaac -ac 2 -ab 64k -f mp4 "ipod/$file.m4a"
fi
done) &

```

---

### Post by FakeOutdoorsman on 2010-02-10
> **markp1989 said:**
> thats slower then what i was using before it only used 40% of 1 core.
Did you compile FFmpeg and x264?  What processor are you using?  Can you show the *using cpu capabilities* line that appears when you start your encode?  Better yet, show the complete FFmpeg output.

Don't give up on libx264 yet.  The example I gave you was optimized for quality over speed.  If you want to encode faster you can change *-vpre* to default, normal, or fastfirstpass (fastfirstpass is the fastest).

---

### Post by markp1989 on 2010-02-10
> **FakeOutdoorsman said:**
> Did you compile FFmpeg and x264?  What processor are you using?  Can you show the *using cpu capabilities* line that appears when you start your encode?  Better yet, show the complete FFmpeg output.

Don't give up on libx264 yet.  The example I gave you was optimized for quality over speed.  If you want to encode faster you can change *-vpre* to default, normal, or fastfirstpass (fastfirstpass is the fastest).

thats for replying again :)

the cpu is an E8400 oced to 4ghz 

here is the complete output running it. 
```
mark@torrentslave:/media/torrents/tv/House/Season6$ ffmpeg -i "/media/torrents/tv/House/Season6/House.S06E13.HDTV.XviD-XII.avi" -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -vpre ipod320 -crf 26 -threads 0 -f ipod  output.mp4 > encodelog
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:35:00, gcc: 4.4.1
Input #0, avi, from '/media/torrents/tv/House/Season6/House.S06E13.HDTV.XviD-XII.avi':
  Duration: 00:43:04.77, start: 0.000000, bitrate: 1134 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x352 [PAR 1:1 DAR 20:11], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
File 'output.mp4' already exists. Overwrite ? [y/N] y
Output #0, ipod, to 'output.mp4':
    Stream #0.0: Video: libx264, yuv420p, 640x352 [PAR 1:1 DAR 20:11], q=10-51, 200 kb/s, 90k tbn, 23.98 tbc
    Stream #0.1: Audio: libfaac, 48000 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x1f418c0]using SAR=1/1
[libx264 @ 0x1f418c0]frame MB size (40x22) > level limit (396)
[libx264 @ 0x1f418c0]DPB size (4 frames, 1351680 bytes) > level limit (2 frames, 912384 bytes)
[libx264 @ 0x1f418c0]VBV buffer (3000) > level limit (2000)
[libx264 @ 0x1f418c0]MB rate (21098) > level limit (11880)
[libx264 @ 0x1f418c0]using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.1 Cache64
[libx264 @ 0x1f418c0]profile Baseline, level 1.3
[ipod @ 0x1f40890]Warning, extension is not .m4a nor .m4v Quicktime/Ipod might not play the file
Press [q] to stop encoding
frame=61972 fps= 55 q=21.0 Lsize=  176797kB time=2584.67 bitrate= 560.4kbits/s    
video:134986kB audio:40377kB global headers:1kB muxing overhead 0.817574%
    Last message repeated 1 times
[libx264 @ 0x1f418c0]slice I:590   Avg QP:19.69  size: 14489
[libx264 @ 0x1f418c0]slice P:61382 Avg QP:22.68  size:  2113
[libx264 @ 0x1f418c0]mb I  I16..4: 31.4%  0.0% 68.6%
[libx264 @ 0x1f418c0]mb P  I16..4:  2.8%  0.0%  0.8%  P16..4: 46.7% 10.7%  3.6%  0.0%  0.0%    skip:35.3%
[libx264 @ 0x1f418c0]coded y,uvDC,uvAC intra:31.3% 50.6% 9.8% inter:7.3% 15.3% 0.1%
[libx264 @ 0x1f418c0]ref P L0  73.0% 13.8%  9.2%  4.0%
[libx264 @ 0x1f418c0]SSIM Mean Y:0.9803900
[libx264 @ 0x1f418c0]kb/s:427.8
mark@torrentslave:/media/torrents/tv/House/Season6$ 
```

im instaling the new ver now

---

### Post by FakeOutdoorsman on 2010-02-10
If you're not going to resize your video you can use the *ipod640* preset instead of *ipod320*.

---

