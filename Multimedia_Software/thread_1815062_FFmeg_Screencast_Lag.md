---
title: "FFmeg Screencast Lag"
date: 2011-07-30
forum: Multimedia Software
---

### Post by io5cml4z on 2011-07-30
Hi. Long story short, I want to start a Minecraft Let's Play series on Youtube, but FFmpeg lags somewhat when recording. The average fps is acceptable, but every few seconds I get these lag spikes, and when I play back the video, they are even longer. I should also mention that RecordMyDesktop works fine with no lag. Here are my system specs:
AMD Phenom II X2 N660 (3.0GHz, Dual Core)
AMD Radeon HD 6470M
4GB RAM
Is my computer not good enough? If so, is there a way that I can record in lower quality? I wouldn't mind that too much. Also, I tried using Fluxbox instead of KDE, and I still got the same lag. Oh, and I also have the proprietary driver installed for my video card (The open source drivers don't support it). Help anyone? :)

---

### Post by io5cml4z on 2011-07-30
Bumpeventhoughtitsnotnecessary

---

### Post by FakeOutdoorsman on 2011-07-30
Please provide your FFmpeg command and the complete terminal output.

---

### Post by io5cml4z on 2011-07-30
Thanks for the quick reply. Here is the command that I use (Mostly, I tried a few variants, some with sound, some without, but there's no difference):
ffmpeg -f x11grab -s 1366x768 -r 30 -i :0.0 -threads 0 -vcodec huffyuv screencast.avi

---

### Post by FakeOutdoorsman on 2011-07-30
> **FakeOutdoorsman said:**
> ...and the complete terminal output.

You forgot this.

---

### Post by io5cml4z on 2011-07-30
Woops. Sorry about that.
```
andrew@andrew-pc:~$ ffmpeg -f x11grab -s 1366x768 -r 30 -i :0.0 -threads 0 -vcodec huffyuv screencast.avi
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2000-2010 the Libav developers
  built on Mar 22 2011 15:55:04 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[x11grab @ 0x155c640]device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1366 height: 768
[x11grab @ 0x155c640]shared memory extension  found
[x11grab @ 0x155c640]Estimating duration from bitrate, this may be inaccurate
Input #0, x11grab, from ':0.0':                                                 
  Duration: N/A, start: 1312063243.087831, bitrate: 1007124 kb/s
    Stream #0.0: Video: rawvideo, bgra, 1366x768, 1007124 kb/s, 30 tbr, 1000k tbn, 30 tbc
File 'screencast.avi' already exists. Overwrite ? [y/N] y
[huffyuv @ 0x156bae0]using huffyuv 2.2.0 or newer interlacing flag
Output #0, avi, to 'screencast.avi':
  Metadata:
    ISFT            : Lavf52.64.2
    Stream #0.0: Video: huffyuv, bgra, 1366x768, q=2-31, 200 kb/s, 30 tbn, 30 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=   17 fps=  0 q=0.0 size=   21278kB time=3.63 bitrate=47974.4kbits/s dup=0frame=   32 fps= 31 q=0.0 size=   40847kB time=4.13 bitrate=80956.1kbits/s dup=0frame=   48 fps= 31 q=0.0 size=   62539kB time=4.67 bitrate=109783.1kbits/s dup=frame=   64 fps= 30 q=0.0 size=   84474kB time=5.20 bitrate=133079.8kbits/s dup=frame=   80 fps= 30 q=0.0 size=  106524kB time=5.73 bitrate=152205.7kbits/s dup=frame=   95 fps= 30 q=0.0 size=  127590kB time=6.23 bitrate=167681.3kbits/s dup=frame=  110 fps= 30 q=0.0 size=  149551kB time=6.73 bitrate=181949.3kbits/s dup=frame=  125 fps= 30 q=0.0 size=  171252kB time=7.23 bitrate=193949.1kbits/s dup=frame=  141 fps= 30 q=0.0 size=  193754kB time=7.77 bitrate=204364.4kbits/s dup=frame=  157 fps= 30 q=0.0 size=  216536kB time=8.30 bitrate=213718.6kbits/s dup=frame=  173 fps= 30 q=0.0 size=  239246kB time=8.83 bitrate=221875.7kbits/s dup=frame=  189 fps= 30 q=0.0 size=  260186kB time=9.37 bitrate=227556.0kbits/s dup=frame=  204 fps= 30 q=0.0 size=  279605kB time=9.87 bitrate=232147.8kbits/s dup=frame=  220 fps= 30 q=0.0 size=  298686kB time=10.40 bitrate=235272.6kbits/s dupframe=  235 fps= 30 q=0.0 size=  316326kB time=10.90 bitrate=237737.8kbits/s dupframe=  250 fps= 30 q=0.0 size=  334936kB time=11.40 bitrate=240684.1kbits/s dupframe=  251 fps= 22 q=0.0 size=  336274kB time=11.43 bitrate=240940.9kbits/s dupframe=  267 fps= 22 q=0.0 size=  358105kB time=15.23 bitrate=192577.2kbits/s dupframe=  282 fps= 22 q=0.0 size=  377627kB time=15.73 bitrate=196622.0kbits/s dupframe=  297 fps= 23 q=0.0 size=  397078kB time=16.23 bitrate=200381.7kbits/s dupframe=  312 fps= 23 q=0.0 size=  416514kB time=16.77 bitrate=203504.0kbits/s dupframe=  327 fps= 23 q=0.0 size=  436686kB time=17.27 bitrate=207181.4kbits/s dupframe=  343 fps= 23 q=0.0 size=  457728kB time=17.80 bitrate=210657.6kbits/s dupframe=  358 fps= 24 q=0.0 size=  476621kB time=18.30 bitrate=213359.6kbits/s dupframe=  374 fps= 24 q=0.0 size=  497795kB time=18.83 bitrate=216527.6kbits/s dupframe=  384 fps= 24 q=0.0 size=  511121kB time=19.37 bitrate=216201.5kbits/s dupframe=  399 fps= 24 q=0.0 size=  531186kB time=19.87 bitrate=219034.1kbits/s dupframe=  406 fps= 24 q=0.0 Lsize=  540562kB time=20.10 bitrate=220312.5kbits/s dup=0 drop=78    
video:540542kB audio:0kB global headers:0kB muxing overhead 0.003641%
Received signal 2: terminating.
```

---

### Post by FakeOutdoorsman on 2011-07-30
Looks like Natty is actually using ffmpeg from Libav and not FFmpeg. Didn't notice before.

Anyway, your lag could be from encoding, decoding, or both. Huffyuv is lossless and creates huge files, but I'm not sure how intensive it is for decoding. To rule out decoding slowness you could re-encode the video to something that is easier to play back:
```
ffmpeg -i screencast.avi -vcodec mpeg2video -qscale 2 -s 682x384 out.mpg
ffplay out.mpg
```
If *out.mpg* plays fine then your issue is with decoding.

Alternatively, you could use use a different encoder such as the method shown here:
[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)

---

### Post by io5cml4z on 2011-07-30
Just tried what you said, and unfortunately it didn't work. I'll check out the link you posted.

---

### Post by io5cml4z on 2011-07-30
(I just thought that I would make a new post so that you see it)
I just tried the link, and it worked INCREDIBLY. There was only one lag spike, and I'm guessing that was just my system (I think I'll be switching to Arch Linux soon, so hopefully I see a small speed boost, and no lag spikes). However: the audio gradually got more and more out of sync. Can you think of any way to fix this?

---

### Post by io5cml4z on 2011-07-31
Bump? Can anyone help me? The audio gradually gets more and more out of sync.

---

### Post by io5cml4z on 2011-07-31
Bump.

---

### Post by io5cml4z on 2011-07-31
I'm just going to mark this as solved and start a new thread.

---

