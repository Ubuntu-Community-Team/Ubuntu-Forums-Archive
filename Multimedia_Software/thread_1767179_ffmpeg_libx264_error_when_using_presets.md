---
title: "ffmpeg: libx264 error when using presets"
date: 2011-05-25
forum: Multimedia Software
---

### Post by sekiryou on 2011-05-25
OS: Ubuntu 10.04 LTS (Lucid Lynx)

Hi guys,
   I have installed the latest ffmpeg using this tutorial : 
[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095").

   What ever I do I always get the same error when trying to use ffmpeg with the new presets setting. I've searched forums and google the whole last day and now I'm pretty lost.

   Here is the command I use (I've stripped it down to it's simplest form.):
```
$ ffmpeg -i ~/Desktop/input.mkv -vcodec libx264 -vpre lossless_slow ~/Desktop/output.mp4
```
and this is the error:
```
[COLOR="Red"][libx264 @ 0xabfec80] constant rate-factor is incompatible with 2pass.[/COLOR]
```
I'm not doing multi-pass encoding?

I've tried changing the bitrate, adding -pass 1, bitrate tolerance, quality based etc... I've tried at least 60 different things... reinstall ffmpeg countless times using different tutorials. It's always the same error. :confused:

Thank you for your help.

---

### Post by ron999 on 2011-05-25
Hi
There's not enough information there.
Paste the command and it's output.

---

### Post by sekiryou on 2011-05-25
Sorry about that, i'm new to all this. Here it is:
```
$ ffmpeg -i ~/Desktop/output.mkv -vcodec libx264 -vpre lossless_slow ~/Desktop/our-final-product.mp4
ffmpeg version git-N-30186-gd9d5603, Copyright (c) 2000-2011 the FFmpeg developers
  built on May 25 2011 00:12:17 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-x11grab --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libdc1394 --enable-libfaac --enable-libgsm --enable-libmp3lame --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-avfilter --enable-pthreads --disable-stripping --enable-runtime-cpudetect --enable-swscale
  libavutil    51.  2. 1 / 51.  2. 1
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2. 10. 0 /  2. 10. 0
  libswscale    0. 14. 0 /  0. 14. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[COLOR="Orange"][matroska,webm @ 0xa7e8b20] Estimating duration from bitrate, this may be inaccurate[/COLOR]

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.97 (30000/1001)
Input #0, matroska,webm, from '/home/sekiryou/Desktop/output.mkv':
  Duration: 00:00:30.83, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264 (High 4:4:4 Predictive), yuv420p, 1680x1050, PAR 1:1 DAR 8:5, 29.97 tbr, 1k tbn, 59.94 tbc (default)
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s (default)
File '/home/sekiryou/Desktop/our-final-product.mp4' already exists. Overwrite ? [y/N] y
[buffer @ 0xa7f1040] w:1680 h:1050 pixfmt:yuv420p tb:1/1000000 sar:1/1 sws_param:
[COLOR="orange"][libx264 @ 0xa7ebc80] --psnr used with psy on: results will be invalid!
[libx264 @ 0xa7ebc80] --tune psnr should be used if attempting to benchmark psnr!
[libx264 @ 0xa7ebc80] interlace + weightp is not implemented[/COLOR]
[libx264 @ 0xa7ebc80] using SAR=1/1
[libx264 @ 0xa7ebc80] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[COLOR="Red"][libx264 @ 0xa7ebc80] constant rate-factor is incompatible with 2pass.[/COLOR]
Output #0, mp4, to '/home/sekiryou/Desktop/our-final-product.mp4':
    Stream #0.0: Video: libx264, yuv420p, 1680x1050 [PAR 1:1 DAR 8:5], q=0-69, pass 1, pass 2, 200 kb/s, 90k tbn, 29.97 tbc (default)
    Stream #0.1: Audio: libfaac, 44100 Hz, 2 channels, s16, pass 1, pass 2, 64 kb/s (default)
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

---

### Post by ron999 on 2011-05-25
Hi
I think that lossless presets are not used for this job.
Instead of **-vpre lossless**, use one of x264's presets.
When you enter [FONT="Courier New"]x264 -h[/FONT] they are listed:-
- > ultrafast,superfast,veryfast,faster,fast,medium,slow,slower,veryslow,placebo

Try them with -crf or -b or whatever.
Something like this:-
```
ffmpeg -i ~/Desktop/output.mkv -vcodec libx264 -preset slow -crf 20 ~/Desktop/our-final-product.mp4
```
Or this:-
```
ffmpeg -i ~/Desktop/output.mkv -vcodec libx264 -preset veryslow -b 500k ~/Desktop/our-final-product.mp4
```

---

### Post by sekiryou on 2011-05-25
> **ron999 said:**
> Hi
I think that lossless presets are not used for this job.
I'm confused about that... Well that's an example I found over Internet. I didn't find any example use in ffmpeg documentation. Do you know any places where they talk about that option?

> **ron999 said:**
> Instead of **-vpre lossless**, use one of x264's presets.
When you enter [FONT="Courier New"]x264 -h[/FONT] they are listed:-

Ok so if I understand I have to use x264 presets not ffmpeg presets. I didn't noticed that in the ffmpeg man page at first, but you're right, there is a libx264 specific section where they talk about the "-preset" option to be used. 

Man Page:
> VIDEO ENCODERS
       A description of some of the currently available video encoders follows.

   libx264
       H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 format supported through libx264.

       Requires the presence of the libx64 headers and library during configuration. You need to explicitely configure the
       build with "--enable-libx264".

       Options

       preset preset_name
           Set the encoding preset.
[...]

> **ron999 said:**
> Try them with -crf or -b or whatever.
Something like this:-
```
ffmpeg -i ~/Desktop/output.mkv -vcodec libx264 -preset slow -crf 20 ~/Desktop/our-final-product.mp4
```
Or this:-
```
ffmpeg -i ~/Desktop/output.mkv -vcodec libx264 -preset veryslow -b 500k ~/Desktop/our-final-product.mp4
```

Done. It worked perfectly, thank you very much for your help ron999.

---

### Post by ron999 on 2011-05-25
> **sekiryou said:**
> 
Ok so if I understand I have to use x264 presets not ffmpeg presets.
Hi
In the folder **usr > local > share > ffmpeg** the ffmpeg presets are found.
It's OK to use the **-vpre ipod320** and **-vpre ipod640** presets.

---

### Post by sekiryou on 2011-05-25
> **ron999 said:**
> Hi
In the folder **usr > local > share > ffmpeg** the ffmpeg presets are found.
It's OK to use the **-vpre ipod320** and **-vpre ipod640** presets.
 
Until I understand what they do and in what conditions, I'll stick with x264 presets ;)
 
Your help was very useful, thanks again.

---

