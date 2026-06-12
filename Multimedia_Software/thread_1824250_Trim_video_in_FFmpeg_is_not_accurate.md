---
title: "Trim video in FFmpeg is not accurate"
date: 2011-08-13
forum: Multimedia Software
---

### Post by ronts on 2011-08-13
I tried to trim a video in FFmpeg using this command:
```
ffmpeg -ss 00:20:48.500 -t 00:01:00 -i INPUT.mp4 -acodec copy -vcodec copy OUTPUT.mp4
```

But FFmpeg is not accurate and it started the video from a nearby point instead (from 00:24:46~). I tried to add 2 seconds to my starting point and it took another frame (not what I wanted).

The video source is H264 video with AAC audio.

Any suggestions what I should do? I need it to be as accurate as possible.

Thanks.

---

### Post by BicyclerBoy on 2011-08-13
The problem maybe..
Simple trim cutting H264 has to be on a I frame..These can be up to seconds apart..

Frame accurate cutting requires a new cut-point I frame to be calculated from the previous I up to the current P or B frame, then new B & P frames must be computed up to next I frame..

I did not know ffmpeg could now cut H264 **at all** without video re-encoding...
This was not possible a year ago.
ffmpeg weakness was it could not cut in the (de)muxer only in the (de)coder.

Try re-encoding with -vcodec libx264 in place of -vcodec copy

This is much slower but you only want a minute..core 2 duo should manage 1-2x real-time.

---

### Post by ronts on 2011-08-14
I tried to put -vcodec libx264, but it's still not accurate.

---

### Post by FakeOutdoorsman on 2011-08-15
> **ronts said:**
> But FFmpeg is not accurate...
Try moving **-ss** past **-i INPUT.mp4** so FFmpeg uses it as an output option. It's slower, but can be more accurate:
```
ffmpeg -t 00:01:00 -i INPUT.mp4 -ss 00:20:48.500 -acodec copy -vcodec copy OUTPUT.mp4
```

---

### Post by ronts on 2011-08-15
Thanks.

It is now much more accurate (from eye view).  But another problem is now occurring: In the output video, the first 1-2 seconds do not show video. Any idea what can cause that?

---

### Post by FakeOutdoorsman on 2011-08-15
Please show your FFmpeg command and the complete terminal output. What player are you using? Does it work as expected with ffplay?

---

### Post by Bachstelze on 2011-08-15
When trimming a video, you must cut at keyframes, or re-encode. All frames between key-frames are a function of the surrounding frames, only key-frames can be decoded on their own. If you trim between key-frames, the first frame of your resulting clip will not be a key-frame, and all the information needed to decode it will not be available.

If you want guaranteed accuracy, do not use -acodec copy.

---

### Post by ronts on 2011-08-15
> **FakeOutdoorsman said:**
> Please show your FFmpeg command and the complete terminal output. What player are you using? Does it work as expected with ffplay?

*Note: I'm trying this in my office, where unfortunately I only have Windows 7 installed.*
My player is VLC player, and I don't think I have ffplay here.

```
C:\ffmpeg\bin>ffmpeg -t 00:01:00 -i input4.mp4 -ss 00:20:48.500 -acodec co
py -vcodec copy OUTPUT.mp4
ffmpeg version N-31627-g9c2651a, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul 23 2011 15:02:13 with gcc 4.6.1
  configuration: --enable-gpl --enable-version3 --enable-memalign-hack --enable-
runtime-cpudetect --enable-avisynth --enable-bzlib --enable-frei0r --enable-libo
pencore-amrnb --enable-libopencore-amrwb --enable-libfreetype --enable-libgsm --
enable-libmp3lame --enable-libopenjpeg --enable-librtmp --enable-libschroedinger
 --enable-libspeex --enable-libtheora --enable-libvorbis --enable-libvpx --enabl
e-libx264 --enable-libxavs --enable-libxvid --enable-zlib
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  9. 0 / 53.  9. 0
  libavformat  53.  6. 0 / 53.  6. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 27. 3 /  2. 27. 3
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[h264 @ 02751E40] Overread VUI by 40 bits
[mov,mp4,m4a,3gp,3g2,mj2 @ 002F9E40] max_analyze_duration 5000000 reached at 501
3333

Seems stream 1 codec frame rate differs from container frame rate: 1200.00 (1200
/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'input.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    creation_time   : 2011-08-10 19:22:14
    encoder         : Sorenson Squeeze 4.5
  Duration: 00:47:46.47, start: 0.000000, bitrate: 1579 kb/s
    Stream #0.0(und): Audio: aac, 48000 Hz, stereo, s16, 128 kb/s
    Metadata:
      creation_time   : 2011-08-10 19:22:14
    Stream #0.1(und): Video: h264 (Constrained Baseline), yuv420p, 640x480, 1446
 kb/s, 25 fps, 25 tbr, 600 tbn, 1200 tbc
    Metadata:
      creation_time   : 2011-08-10 19:22:14
    Stream #0.2(und): Data: mp4s / 0x7334706D
    Metadata:
      creation_time   : 2011-08-10 20:08:43
    Stream #0.3(und): Data: mp4s / 0x7334706D
    Metadata:
      creation_time   : 2011-08-10 20:08:43
strptime() unavailable on this system, cannot convert the date string.
Output #0, mp4, to 'OUTPUT.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    creation_time   : 2011-08-10 19:22:14
    encoder         : Lavf53.6.0
    Stream #0.0(und): Video: libx264, yuv420p, 640x480, q=2-31, 1446 kb/s, 600 t
bn, 600 tbc
    Metadata:
      creation_time   : 2011-08-10 19:22:14
    Stream #0.1(und): Audio: aac, 48000 Hz, stereo, 128 kb/s
    Metadata:
      creation_time   : 2011-08-10 19:22:14
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop, [?] for help
frame=    0 fps=  0 q=-1.0 size=       0kB time=00:00:00.00 bitrate=   0.0kbits/
frame=    0 fps=  0 q=-1.0 size=       0kB time=00:00:00.00 bitrate=   0.0kbits/
frame=    0 fps=  0 q=-1.0 size=       0kB time=00:00:00.00 bitrate=   0.0kbits/
frame=    0 fps=  0 q=-1.0 size=       0kB time=00:00:00.00 bitrate=   0.0kbits/
frame=    0 fps=  0 q=-1.0 size=       0kB time=00:00:00.00 bitrate=   0.0kbits/
frame=    0 fps=  0 q=-1.0 size=       0kB time=00:00:00.00 bitrate=   0.0kbits/
frame=    0 fps=  0 q=-1.0 size=       0kB time=00:00:00.00 bitrate=   0.0kbits/
frame=    0 fps=  0 q=-1.0 size=       0kB time=00:00:00.00 bitrate=   0.0kbits/
frame=    0 fps=  0 q=-1.0 size=       0kB time=00:00:00.00 bitrate=   0.0kbits/
frame= 1500 fps=303 q=-1.0 Lsize=   12020kB time=00:00:59.98 bitrate=1641.6kbits
/s
video:11048kB audio:937kB global headers:0kB muxing overhead 0.292158%
```


> **Bachstelze said:**
> When trimming a video, you must cut at keyframes, or re-encode. All frames between key-frames are a function of the surrounding frames, only key-frames can be decoded on their own. If you trim between key-frames, the first frame of your resulting clip will not be a key-frame, and all the information needed to decode it will not be available.

If you want guaranteed accuracy, do not use -acodec copy.

Then what should I use instead?

---

### Post by shantiq on 2011-08-17
in recent times i have found mencoder to be more accurate for this type of job

```
sudo apt-get install mencoder
```



then use this syntax

```
mencoder  -ss 01:00:00  -endpos 00:05:56 -oac copy -ovc copy nameoffile.mp4 -o nameoftrimmedfile.mp4
```


or you may be asked to use pcm for audio then change to


```
mencoder  -ss 01:00:00  -endpos 00:05:56 -oac pcm -ovc copy nameoffile.mp4 -o nameoftrimmedfile.mp4
```







see how that works :KS

---

