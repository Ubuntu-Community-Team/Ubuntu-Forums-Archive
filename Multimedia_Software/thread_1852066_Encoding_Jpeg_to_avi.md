---
title: "Encoding Jpeg to avi"
date: 2011-09-29
forum: Multimedia Software
---

### Post by lucacerone on 2011-09-29
Hi everybody,
I've a set of images called Frame00001.jpeg, Frame00002.jpeg ... 
for a total of 4000 frames.
They are simple images made of just 4 colours.
I'd like to encode them in a video of 640x480 pixels and with reasonable size. 

At the moment I use ffmpeg like this
```
ffmpeg -r 8 -i Frame%05d.jpeg  -b 1200kb -vcodec mpeg4 -an -mbd 2 -flags +4mv -trellis 2 -s 640x480 output.avi 
```
The result has the right dimension and looks great, but the size is too
big! Approximately 42mb for the final avi file.
Fiction episodes that last 21 min have a size of about 175mb and are much more complicated than my videos and have a higher resolution, so there must be some way to reduce the size for my viedo!

I've tried a lot of options for ffmpeg without any proper success.

Have you guys any suggestion for me?

Thanks a lot in advance for your help,
Best Wishes
Luca

---

### Post by FakeOutdoorsman on 2011-09-30
> **lucacerone said:**
> Have you guys any suggestion for me?
Use a more efficient encoder such as x264:
```
ffmpeg -r 8 -i Frame%05d.jpeg -vcodec libx264 -vpre medium -crf 24 -threads 0 -s 640x480 output.mp4
```
The native mpeg4 encoder in FFmpeg won't give you the performance and quality per bitrate as x264 will. See for a more detailed explanation of these options see posts #5 and #7 at:

[Could someone lend me a few instructions for Mencoder and CLi encoding with ffmpeg](http://ubuntuforums.org/showthread.php?t=1847410)

Note that you may have to enable libx264 in FFmpeg. You can do that by installing one package and it's explained in Option B or Option C here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by WasMeHere on 2011-09-30
> **FakeOutdoorsman said:**
> Use a more efficient encoder such as x264:
.../url] +1

I use [_Openshot_]("http://ubuntuforums.org/showpost.php?p=11252744&postcount=6") to edit as well as convert videos. So you can easily do some post-processing, once you have a video of sufficient quality.

---

### Post by lucacerone on 2011-09-30
Dear FakeOutdoorsman,
thank you very much! You made my day!
I didn't mention that I tried to use libx264 but I got some errors before.
But your command worked flawlessly and I could reduce the size of a factor 10!!!
Thanks a lot again,
I'm going through the link you've sent to me and try to understand the option you have used! (and if I don't understand something can I come back and ask to you?)
Have a nice day,
Luca

---

### Post by lucacerone on 2011-09-30
Thanks Olle, I'll keep your advice in mind as well :)

---

### Post by lucacerone on 2011-09-30
Hi FakeOutdoorsman,
I'm sorry to bother you once again, I just noticed that the last couple of frames
(though correctly encoding) are not shown in the final video.
Is there a way to see all the frame in the final video???
Thanks a lot in advance for the help.
Cheers, -Luca

---

### Post by FakeOutdoorsman on 2011-09-30
That does't seem right. What player are you using? Does another player such as *ffplay* show all of the frames? Can you show your FFmpeg command and the complete terminal output?

---

### Post by SeijiSensei on 2011-09-30
Could be an issue with ["B" frames]("http://en.wikipedia.org/wiki/Video_compression_picture_types").

Video compressors like H.264 are based on differencing between frames. There are complete frames interspersed throughout the file, but the adjacent frames are created by differencing the current frame against the full frames.  

Try duplicating the last couple of frames a few times and see if that helps.

Also AVI is an unusual container for H.264; most AVI's contain files in DivX, XviD, or some of the older Microsoft formats.  You might want to consider mp4 or Matroska (mkv) instead of AVI if the player you intend to use supports one of those formats.  Just change output.avi to output.mp4 or output.mkv.

---

### Post by lucacerone on 2011-10-01
Thanks FakeOutdoorsman and SeijiSensei
Here is the encoding command:
```
ffmpeg -y -r 25 -i Frame%05d.png -vcodec libx264 -vpre max  -crf 32 -threads 2 -s 640x480 test1.avi
```
and here is the output:

```
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1.1, Copyright (c) 2000-2010 the Libav developers
  built on Sep 16 2011 16:57:46 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6.2-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6.2-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[image2 @ 0x9800bc0]max_analyze_duration reached
Input #0, image2, from 'Frame%05d.png':
  Duration: 00:00:40.04, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: png, rgb24, 1867x1400, 25 fps, 25 tbr, 25 tbn, 25 tbc
[libx264 @ 0x9825e10]using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0x9825e10]profile High, level 3.2
Output #0, avi, to 'test1.avi':
  Metadata:
    ISFT            : Lavf52.64.2
    Stream #0.0: Video: libx264, yuv420p, 640x480, q=10-51, 200 kb/s, 25 tbn, 25 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    4 fps=  0 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=    7 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   10 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   13 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   16 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   19 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   22 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   25 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   28 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   31 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   34 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   37 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   40 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   43 fps=  6 q=-1.0 size=       6kB time=10000000000.00 bitrate=   0.0kbiframe=   46 fps=  6 q=37.0 size=       8kB time=10000000000.00 bitrate=   0.0kbiframe= 1001 fps=  4 q=-1.0 Lsize=     146kB time=40.00 bitrate=  29.9kbits/s    
video:116kB audio:0kB global headers:0kB muxing overhead 25.343340%
[libx264 @ 0x9825e10]frame I:5     Avg QP:30.39  size:  2126
[libx264 @ 0x9825e10]frame P:294   Avg QP:35.58  size:   156
[libx264 @ 0x9825e10]frame B:702   Avg QP:38.10  size:    89
[libx264 @ 0x9825e10]consecutive B-frames:  0.2%  7.8% 28.9% 63.1%
[libx264 @ 0x9825e10]mb I  I16..4: 53.2% 41.6%  5.2%
[libx264 @ 0x9825e10]mb P  I16..4:  1.6%  2.7%  0.0%  P16..4:  2.8%  0.3%  0.0%  0.0%  0.0%    skip:92.6%
[libx264 @ 0x9825e10]mb B  I16..4:  0.4%  0.3%  0.0%  B16..8:  2.9%  0.1%  0.0%  direct: 0.0%  skip:96.3%  L0:62.3% L1:37.2% BI: 0.5%
[libx264 @ 0x9825e10]8x8 transform intra:53.7% inter:25.1%
[libx264 @ 0x9825e10]direct mvs  spatial:4.6% temporal:95.4%
[libx264 @ 0x9825e10]coded y,uvDC,uvAC intra: 1.2% 0.2% 0.2% inter: 0.0% 0.0% 0.0%
[libx264 @ 0x9825e10]i16 v,h,dc,p: 41% 58%  1%  0%
[libx264 @ 0x9825e10]i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 11%  2% 87%  0%  0%  0%  0%  0%  0%
[libx264 @ 0x9825e10]i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 32% 22% 34%  2%  1%  2%  1%  3%  2%
[libx264 @ 0x9825e10]i8c dc,h,v,p: 99%  1%  1%  0%
[libx264 @ 0x9825e10]Weighted P-Frames: Y:0.0%
[libx264 @ 0x9825e10]ref P L0: 54.4%  0.7%  9.5%  6.4%  4.2%  3.9%  4.5%  2.0%  2.1%  1.8%  1.7%  1.7%  1.8%  1.6%  2.1%  1.5%
[libx264 @ 0x9825e10]ref B L0: 32.5% 14.4% 11.6%  5.2%  4.2%  5.3%  5.7%  2.1%  2.7%  2.5%  2.5%  3.0%  2.3%  2.7%  3.3%
[libx264 @ 0x9825e10]kb/s:23.80
```

Any advice is greatly appreciated :)
Have a nice weekend!

---

### Post by FakeOutdoorsman on 2011-10-01
I agree with SeijiSensei that it could be an issue with b-frames in AVI. This container format should not be used with H.264 with b-frames enabled which I think would be present with the preset you chose. If you must use AVI, then use a different encoder.

My example earlier in this thread used MP4 container format. You should try that instead, as SeijiSensei already mentioned.

Also, you never ruled out the possibility that your player could be introducing the problem.

As for your command you should use one of the following presets: ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow.

The legacy presets were unfortunately not removed in time before being packaged by Ubuntu. The legacy presets are: default, fastfirstpass, hq, max, normal, and slowfirstpass.

Consider changing *-threads 2* to *-threads 0*. This does not mean, "use zero threads", but will allow libx264 to automatically choose an appropriate value.

---

### Post by lucacerone on 2011-10-01
Thanks, I think it wasn't a matter of container or b-frames :)
I've tried to open it with Mplayer and the movie displays all the frames!
Thanks for your help guys!

---

