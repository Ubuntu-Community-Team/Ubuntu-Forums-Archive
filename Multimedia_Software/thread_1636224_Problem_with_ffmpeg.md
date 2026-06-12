---
title: "Problem with ffmpeg"
date: 2010-12-02
forum: Multimedia Software
---

### Post by GammaPoint on 2010-12-02
Hi,

I'm trying to create a movie with a collection of *png files that I created with ImageMagick's 'convert' program. But ffmpeg is crashing. I'm running on the latest version of Ubuntu and just downloaded ffmpeg from the repo. Any idea what the problem might be? The output is below.

Thanks for your time!

```

ME@ME:~/my_dir$ ffmpeg -r 10 -b 1800 -i %04d.png test.mp4
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:35:47 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, image2, from '%04d.png':
  Duration: 00:00:02.00, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: png, y400a, 720x504, 10 fps, 10 tbr, 10 tbn, 10 tbc
File 'test.mp4' already exists. Overwrite ? [y/N] y
swScaler: y400a is not supported as input pixel format
Cannot get resampling context
```

Thanks,
GP

---

### Post by FakeOutdoorsman on 2010-12-05
Can you provide one of the png files?  Also, show the output of:
```
ffmpeg -pix_fmt list
```

Maverick's FFmpeg should show:
```
..... y400a                  2            16
```

But if you compile a recent FFmpeg, you'll probably see:
```
I.... y400a                  2            16
```

The **I** is the only difference:
```
I.... = Supported Input  format for conversion
```

If you want to compile FFmpeg from SVN see:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

I can't guarantee that compiling a newer FFmpeg will work but it's worth a try.

**Edit:** You should also remove the **-b 1800**. You're applying it as an input option where it is now.  Also, **-qscale** is usually a more useful option than **-b**, unless you want to perform a two-pass encode, and you generally only need to do a two-pass if you are trying to get a specific output file size.  For **-qscale**, 2 is roughly visually lossless and 3-5 is a good balance between size and quality. Don't use -qscale with x264 however.

---

### Post by GammaPoint on 2010-12-05
Hi FakeOutdoorsman, 

Thanks for your response! I actually got the thing to work by simply generated jpg files instead of png files. I would upload the png file except the image is part of a research project that is currently unpublished.

As you say, with Maverick I see the pix_fmt list with no I there.

Thanks for the pointers about the -b options and whatnot. I was simply following the instructions on [this website]("http://electron.mit.edu/~gsteele/ffmpeg/") and am not familiar with the best ffmpeg options to use. 

Best,
GP

---

### Post by FakeOutdoorsman on 2010-12-05
What format do you want the output to be? I can give some suggestions depending on your required format.

---

### Post by GammaPoint on 2010-12-05
> **FakeOutdoorsman said:**
> What format do you want the output to be? I can give some suggestions depending on your required format.

I am trying to generate a mp4 movie from a series of still images. I don't really care what the intermediate image format is or even really that it's mp4 as long as the movie works correctly. When I generated the movie with the *jpg images instead of the *png images ffmpeg worked correctly and gave me the desired mp4 movie.

---

### Post by FakeOutdoorsman on 2010-12-05
I generally recommend using png instead because jpg might have some visible compression artifacts, but if the source images don't look any different to you then the jpg should be fine. For the MP4 container format, I recommend encoding to H.264 video.  See the **one-pass CRF** example at [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095).

---

### Post by GammaPoint on 2010-12-05
> **FakeOutdoorsman said:**
> I generally recommend using png instead because jpg might have some visible compression artifacts, but if the source images don't look any different to you then the jpg should be fine. For the MP4 container format, I recommend encoding to H.264 video.  See the **one-pass CRF** example at [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095).

Okay, thanks FakeOutdoorsman, I'll check out the HOWTO that you mentioned. 

The graphics I have look okay, but they are simply some graphs so there's not much that can go wrong. For higher quality images which I sometimes do I'll remember to prefer png.

---

