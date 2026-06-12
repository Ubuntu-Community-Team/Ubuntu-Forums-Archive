---
title: "ffmpeg convert MTS to MP4 problem"
date: 2011-10-20
forum: Multimedia Software
---

### Post by fnadde42 on 2011-10-20
Hello forum!
I have this really bad camcorder that records in high quality. Then why is it bad then? Because it records in some iditot codec that is impossible to edit with. So I want to convert this, so called, _AVCHD video_ into _MPEG4 video_ so I can actually do something with my recorded material. I have looked around and a lot of people are recommending ffmpeg. So I installed it and tried it on one of my clips.

I'm gonna warn you right now; I'm kind of a n00b when it comes to this.

But anyway, this is what I typed in the terminal

The output of this was a video named [FONT="Courier New"]output.mp4 - 0 bytes - MPEG-4-video[/FONT] 

```
**ffmpeg -i 00000.MTS -vframes 25 -s hd1080 -vcodec mpeg4 -deinterlace output.mp4**
ffmpeg version 0.7.2-4:0.7.2-1ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Oct  2 2011 15:13:26 with gcc 4.6.1
  configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.2.1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  avcodec     configuration: --extra-version='4:0.7.2.1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  5. 0 / 53.  5. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 50.00 (50/1)
Input #0, mpegts, from '00000.MTS':
  Duration: 00:00:09.63, start: 0.801367, bitrate: 16846 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 50 fps, 50 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
[buffer @ 0xb7a9e0] w:1920 h:1080 pixfmt:yuv420p
[COLOR="Red"][libvo_aacenc @ 0xb77940] Unable to set encoding parameters[/COLOR]
Output #0, mp4, to 'output.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 50 tbc
    Stream #0.1: Audio: libvo_aacenc, 48000 Hz, 5.1, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

---

### Post by FakeOutdoorsman on 2011-10-20
The not so useful error is coming from *libvo_aacenc*. I guess it is having trouble with the input having 6 channels. You can try adding **-acodec copy** and copy the input audio to the output. Or add **-ac 2** to attempt to downmix from 6 to 2 channels (stereo). This is not compatible with **-acodec copy** and will re-encode your audio into a lossy format therefore will have lower quality, but you may not notice a difference with a high enough bitrate (**-ab 192k** for example).

As for the video, add **-qscale 3** to improve the output quality. The default output bitrate of 200k is dismal. You can also remove **-s hd1080** because your output will automatically inherit the frame size of the input.

What editor is having trouble with your inputs? It's doubtful, but perhaps the container is to blame:
```
ffmpeg -i 00000.MTS -vcodec copy -acodec copy 00000.mp4
```
or
```
ffmpeg -i 00000.MTS -vcodec copy -acodec copy 00000.mkv
```

---

### Post by fnadde42 on 2011-10-20
I'm using Kdenlive. I know that it can open .MTS-files but it freezes Kdenlive for a few seconds when you try to play through the timeline. So I want to convert it to a better format for editing.

I tried the first command and the result is the same; it generate a file that's less than 1Kb

But the other one with the Matroska container worked! Thanks a thousand times!

---

### Post by pollywog on 2012-06-18
I used WinFF (version 1.4.2 running on Lucid) and it worked like a charm

---

