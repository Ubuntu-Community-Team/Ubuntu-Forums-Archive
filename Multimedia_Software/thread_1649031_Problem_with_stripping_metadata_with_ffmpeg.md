---
title: "Problem with stripping metadata with ffmpeg"
date: 2010-12-19
forum: Multimedia Software
---

### Post by denarced on 2010-12-19
Hei,

I have a lot of avis with annoying metadata that show in vlc.
Since I cannot figure out how to configure vlc in a way that it won't show the tags, ffmpeg should strip the tags.
This is supposed to do the trick:
```

ffmpeg -metadata title="" -acodec copy -vcodec copy -i original.avi new.avi

```

This operation creates the output:

```

denarced@denarced-desktop:~/f/Desktop$ ffmpeg -metadata title="" -acodec copy -vcodec copy -i original.avi new.avi
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:36:53 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, avi, from 'original.avi':
  Metadata:
    INAM            : DEAD LIKE ME S1 D4 US.Title4.DVDRip
    IART            : DiannaBarfield
    IPRD            : DEAD LIKE ME S1 D4 US
    ISFT            : Lavf51.10.0
  Duration: 00:40:51.86, start: 0.000000, bitrate: 1350 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 768x432 [PAR 1:1 DAR 16:9], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Output #0, avi, to 'new.avi':
  Metadata:
    INAM            : 
    ISFT            : Lavf52.64.2
    Stream #0.0: Video: mpeg4, yuv420p, 768x432 [PAR 1:1 DAR 16:9], q=2-31, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=25805 fps=4137 q=-1.0 size=  182199kB time=1076.26 bitrate=1386.8kbits/s   frame=27773 fps=4125 q=-1.0 size=  193618kB time=1158.34 bitrate=1369.3kbits/s   frame=30022 fps=4107 q=-1.0 size=  206417kB time=1252.13 bitrate=1350.5kbits/s   frame=32159 fps=4042 q=-1.0 size=  219859kB time=1341.30 bitrate=1342.8kbits/s   frame=32742 fps=4014 q=-1.0 size=  223769kB time=1365.60 bitrate=1342.4kbits/s   frame=36327 fps=3944 q=-1.0 size=  247507kB time=1515.10 bitrate=1338.2kbits/s   frame=36327 fps=3944 q=-1.0 size=  247513kB time=1515.14 bitrate=1338.2kbits/s   frame=41883 fps=3905 q=-1.0 size=  282452kB time=1746.87 bitrate=1324.6kbits/s   frame=41884 fps=3886 q=-1.0 size=  282454kB time=1746.88 bitrate=1324.6kbits/s   frame=46525 fps=3823 q=-1.0 size=  316367kB time=1940.45 bitrate=1335.6kbits/s   frame=46525 fps=3806 q=-1.0 size=  316380kB time=1940.48 bitrate=1335.6kbits/s   frame=50351 fps=3729 q=-1.0 size=  346324kB time=2100.06 bitrate=1351.0kbits/s   frame=50352 fps=3702 q=-1.0 size=  346326kB time=2100.06 bitrate=1351.0kbits/s   frame=54149 fps=3645 q=-1.0 size=  374967kB time=2258.46 bitrate=1360.1kbits/s   frame=54150 fps=3629 q=-1.0 size=  374970kB time=2258.50 bitrate=1360.1kbits/s   frame=58786 fps=3620 q=-1.0 Lsize=  404062kB time=2451.87 bitrate=1350.0kbits/s    
video:266757kB audio:134092kB global headers:0kB muxing overhead 0.801432%

```

I don't know anything about ffmpeg or video editing but the audio is ****ed up after the operation. Vlc simply says that the codec "undf" is not supported.

It does pop out that the ISFT value has changed.

Anyone know the solution ?

---

### Post by denarced on 2010-12-19
More info:

```

denarced@denarced-desktop:~/f/Desktop$ cmp -b new.avi original.avi 
new.avi original.avi differ: byte 5, line 1 is 350 M-h 274 M-<

```

```

denarced@denarced-desktop:~/f/Desktop$ ls -l new.avi original.avi 
-rw-r--r-- 1 denarced denarced 413759472 2010-12-19 23:07 new.avi
-rw-r--r-- 1 denarced denarced 413759428 2010-12-19 22:15 original.avi

```

---

### Post by ron999 on 2010-12-19
Hi
Change your command so that it's like this and try again:-
```
ffmpeg -i original.avi -vcodec copy -acodec copy new.avi
```

---

### Post by denarced on 2010-12-20
> **ron999 said:**
> Hi
Change your command so that it's like this and try again:-
```
ffmpeg -i original.avi -vcodec copy -acodec copy new.avi
```

Tried it out:
```

denarced@denarced-desktop:~/f/Desktop$ ffmpeg -i original.avi -vcodec copy -acodec copy new.avi 
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:36:53 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, avi, from 'original.avi':
  Metadata:
    INAM            : DEAD LIKE ME S1 D4 US.Title4.DVDRip
    IART            : DiannaBarfield
    IPRD            : DEAD LIKE ME S1 D4 US
    ISFT            : Lavf51.10.0
  Duration: 00:40:51.86, start: 0.000000, bitrate: 1350 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 768x432 [PAR 1:1 DAR 16:9], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
File 'new.avi' already exists. Overwrite ? [y/N] y
Output #0, avi, to 'new.avi':
  Metadata:
    ISFT            : Lavf52.64.2
    Stream #0.0: Video: mpeg4, yuv420p, 768x432 [PAR 1:1 DAR 16:9], q=2-31, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=26306 fps=4352 q=-1.0 size=  185110kB time=1097.18 bitrate=1382.1kbits/s   frame=27326 fps=3872 q=-1.0 size=  191192kB time=1139.71 bitrate=1374.2kbits/s   frame=35181 fps=4396 q=-1.0 size=  239779kB time=1467.34 bitrate=1338.7kbits/s   frame=36383 fps=4466 q=-1.0 size=  247861kB time=1517.47 bitrate=1338.1kbits/s   frame=43441 fps=4847 q=-1.0 size=  292880kB time=1811.84 bitrate=1324.2kbits/s   frame=44733 fps=4762 q=-1.0 size=  302724kB time=1865.74 bitrate=1329.2kbits/s   frame=46852 fps=4819 q=-1.0 size=  319379kB time=1954.11 bitrate=1338.9kbits/s   frame=51706 fps=4975 q=-1.0 size=  356017kB time=2156.54 bitrate=1352.4kbits/s   frame=53129 fps=4971 q=-1.0 size=  367672kB time=2215.90 bitrate=1359.3kbits/s   frame=54264 fps=4485 q=-1.0 size=  375733kB time=2263.23 bitrate=1360.0kbits/s   frame=54590 fps=4496 q=-1.0 size=  377954kB time=2276.86 bitrate=1359.9kbits/s   frame=58786 fps=4669 q=-1.0 Lsize=  404062kB time=2451.87 bitrate=1350.0kbits/s    
video:266757kB audio:134092kB global headers:0kB muxing overhead 0.801432%

```

No difference to speak of.

---

### Post by denarced on 2010-12-20
In fact, the result of ron999's command lead into exactly the same result. I verified this with md5sum.

More precisely, the following commands are functionally identical:
```

ffmpeg -metadata title="" -acodec copy -vcodec copy -i original.avi new.avi
ffmpeg -i original.avi -metadata title="" -vcodec copy -acodec copy new.avi

```

---

### Post by denarced on 2010-12-22
It would appear that the problem has nothing to do with the metadata definitions. The audio is messed up even when creating a straight up copy
```

ffmpeg -acodec copy -vcodec copy -i original.avi new.avi

```

---

### Post by FakeOutdoorsman on 2010-12-22
> **denarced said:**
> In fact, the result of ron999's command lead into exactly the same result. I verified this with md5sum.

More precisely, the following commands are functionally identical:
```

ffmpeg -metadata title="" -acodec copy -vcodec copy -i original.avi new.avi
ffmpeg -i original.avi -metadata title="" -vcodec copy -acodec copy new.avi

```
You're applying *-acodec copy -vcodec copy* as input options. Although FFmpeg seems to interpret them as output options.  As for the audio issue, try using a different output container, such as mkv instead of avi.

When using a different output container you can tell that the commands do not lead to an identical result.

```
ffmpeg -i IronMan.mkv -vcodec copy -acodec copy output1.mkv
ffmpeg -vcodec copy -acodec copy -i IronMan.mkv output2.mkv

$ md5sum output*
16f94870c98ee828d1b2e4f1b758c9cc  output1.mkv
b5aaa9011d2a74c093f7dabcb8fd45c2  output2.mkv
```

---

### Post by denarced on 2010-12-22
> **FakeOutdoorsman said:**
> You're applying *-acodec copy -vcodec copy* as input options. Although FFmpeg seems to interpret them as output options.  As for the audio issue, try using a different output container, such as mkv instead of avi.

When using a different output container you can tell that the commands do not lead to an identical result.

```
ffmpeg -i IronMan.mkv -vcodec copy -acodec copy output1.mkv
ffmpeg -vcodec copy -acodec copy -i IronMan.mkv output2.mkv

$ md5sum output*
16f94870c98ee828d1b2e4f1b758c9cc  output1.mkv
b5aaa9011d2a74c093f7dabcb8fd45c2  output2.mkv
```

And we have a winner.
Apparently I don't even have to define the metadata :)
Once the output container is mkv, it automatically inserts the filename as the title and that's that.
Audio is good, everything's good :D

Thanks for everyone who has participated and in particular to FakeOutdoorsman.

Now I can finally start figuring out all the videos with custom titles and all that crap and then create one monster of a script to eliminate the problem..

---

### Post by mkedzierski on 2012-08-08
The *–map_metadata* argument allows copying global/stream metadata from input to output.  If you use –1 as the input file it will strip the specified metadata.  so to strip metadata from global, video and audio streams do the following:
 
```
ffmpeg –i movie.mp4  -c copy –map_metadata:g –1:g  -map_metadata:s:v –1:g –map_metadata:s:a –1:g movie.nometadata.mp4
```

---

