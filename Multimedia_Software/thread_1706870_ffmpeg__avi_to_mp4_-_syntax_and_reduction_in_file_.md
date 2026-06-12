---
title: "ffmpeg : avi to mp4 - syntax and reduction in file size question"
date: 2011-03-14
forum: Multimedia Software
---

### Post by uncle-c on 2011-03-14
HI,
I'm using a basic ffmpeg command to convert some avis into mp4 :
[COLOR="Blue"]file01.avi - 544x416, 368MB[/COLOR]

```

$ ffmpeg -i file01.avi -vb 750k -s 432x336 file01.vb750.432x336.mp4

```

After conversion :
[COLOR="Blue"]file01.vb750.432x336.mp4 - 432x336, 302Mb.[/COLOR]

If I alter the output file dimensions to 352x272 I then get a file size of 301MB, which is just 1MB less than the file of dimensions 432x336 ? I had expected size to be 30-40MB lower. I do not want to compromise quality by reducing the bitrate to below 750 kb/s so how can I alter the ffmpeg command syntax to get a considerably smaller file size with video dimensions 352x272 ?
I would like to use the default codecs and avoid x264 for the mean time.
Regards,
UC

---

### Post by FakeOutdoorsman on 2011-03-14
Can you show the complete output of:
```
ffmpeg -i file01.avi
```
It will provide some useful information on the input. Why do you want to avoid x264?

---

### Post by uncle-c on 2011-03-14
Thanks Fake* , here is the output :

```

unclec@linux:~/Desktop$ ffmpeg -i file01.avi
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Apr 23 2010 15:04:14, gcc: 4.3.2
Input #0, avi, from 'file01.avi':
  Duration: 00:50:53.1, start: 0.000000, bitrate: 961 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 544x416 [PAR 1:1 DAR 17:13], 25.00 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Must supply at least one output file

```

The reason for avoiding x264 is that it will probably take twice as long to encode and it requires far more tinkering on the command line before you get the desired results. I am trying to avoid getting bogged down in heavy command line syntax and the numerous options. But if you can persuade me otherwise I will give it a go.

Cheers.

---

### Post by FakeOutdoorsman on 2011-03-14
I find x264 easier to use and get the results I want. Is there a specific file size you want for the output?

---

### Post by uncle-c on 2011-03-15
Yes Fake,
I would like to reduce the video dimensions to approx 352x272, have good quality i.e. high-ish video bitrate and a size of approx 200-250MB. The running time of the avi is 50 minutes. If x264 solution is best than some good command line parameters to use would be most helpful.

TIA
UC

---

### Post by rubylaser on 2011-03-15
Here are some simple examples using ffmpeg and x264.
[http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/]("http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/")
You'll only need to add the size option to scale them down.
```
-s 352x272
```

x264 perfect for encoding to a smaller size, while maintaining visual quality.  If you really want to hit a specific max size, you can calculate the necessary bitrate based on the runtime, and use a 2 pass encode, or use a script like this...

[http://www.helyar.net/2009/ffmpeg-target-file-sizes-again/]("http://www.helyar.net/2009/ffmpeg-target-file-sizes-again/")

---

### Post by uncle-c on 2011-03-15
Thanks RL.
I've had to try the above on my 10.10 box, unfortunately, I get "unknown encoder" errors. I have the x264 encoder installed and have tried all the following :

```
 $ ffmpeg -i input.avi .... -vcodec [x264|h264|libx264|H264|H.264|h.264] ... output.mp4 
```
 
but to no avail. However,  I can encode with the h264 / x264 when using Handbrake to do the encoding / resizing.  Now I'm confused as to why the ffmpeg command does not recognise the codec ??

EDIT: All the following are installed :

libx264-98 - x264 video coding library
libx264-dev - development files for libx264
x264 - video encoder for the H.264/MPEG-4 AVC standard

```


unclec@linux:~$ ffmpeg -i chro.avi  -vcodec libx264  -s 320x240 chro.mp4
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:35:47 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  [COLOR="Red"]WARNING: library configuration mismatch[/COLOR]
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
[mpeg4 @ 0x9724650]Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from 'chro.avi':
  Duration: 00:03:57.29, start: 0.000000, bitrate: 282 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 15 tbr, 18.04 tbn, 15 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 128 kb/s
Unknown encoder 'libx264'

```

@Fake* I read a previous post of yours the "WARNING: library configuration mismatch" error may be a pointer to something not quite correct. Perhaps a purge and reinstallation of FFMPEG ?

---

### Post by FakeOutdoorsman on 2011-03-15
> **uncle-c said:**
> @Fake* I read a previous post of yours the "WARNING: library configuration mismatch" error may be a pointer to something not quite correct. Perhaps a purge and reinstallation of FFMPEG ?

You can ignore that warning. You need to install one package to get the repository FFmpeg to encode with *libx264* and *libfaac*. See **Option C** in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

You want an output of ~200 MB for a 50 minute duration video. file size / duration = bitrate.

(200 MB * 8192 [converts MB to kilobits]) / 3000 seconds = ~544k total bitrate
544k total bitrate - 128k audio bitrate = 416k video bitrate

Example:
```
ffmpeg -i input -vcodec libx264 -vpre medium_firstpass -b 416k -threads 0 -pass 1 -an -f mp4 -y /dev/null && ffmpeg -i input -vcodec libx264 -vpre medium -b 416k -threads 0 -pass 2 -acodec libfaac -ab 128k output.mp4
```

I hardly ever use two-pass encoding. Only when I'm targeting a specific output file size. Otherwise I use single pass CRF as shown here: [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

---

### Post by uncle-c on 2011-03-16
Nice one Fake, now we are getting somewhere. I think we have almost reached the holy grail except I get this perennial error :

```
 File for preset 'medium_fastfirstpass' not found 
```

EDIT: Fixed the above problem , just needed to copy all the presets from /usr/share/ffmpeg to ~/.ffmpeg/

Just experimenting with some settings in order to get the correct balance of bitrate , file size and quality.
Many thanks RL & Fake for the joint successful effort.

Another very useful ffmpeg link :

[http://juliensimon.blogspot.com/2009/01/howto-ffmpeg-x264-presets.html]("http://juliensimon.blogspot.com/2009/01/howto-ffmpeg-x264-presets.html")

---

### Post by FakeOutdoorsman on 2011-03-16
Oops. That was a typo. It should be **-vpre medium_firstpass**. I fixed it in the example command. I recommend removing *~/.ffmpeg*, because in the rare chance that the presets are updated upstream and you update FFmpeg you will still be using outdated presets.

---

### Post by uncle-c on 2011-03-16
> **FakeOutdoorsman said:**
> Oops. That was a typo. It should be **-vpre medium_firstpass**. I fixed it in the example command. I recommend removing *~/.ffmpeg*, because in the rare chance that the presets are updated upstream and you update FFmpeg you will still be using outdated presets.

Good one, will do !

Thanks again !
uc

---

