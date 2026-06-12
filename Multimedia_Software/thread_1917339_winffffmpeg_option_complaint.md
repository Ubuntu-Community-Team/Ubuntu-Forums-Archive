---
title: "winff/ffmpeg option complaint"
date: 2012-01-29
forum: Multimedia Software
---

### Post by shortmort37 on 2012-01-29
I recently upgraded to 11.10, and tried to convert an ogv file with winff.  I got this complaint, with full details below:

> [NULL @ 0x991d360] Unable to parse option value "1000kb"
Invalid value '1000kb' for option 'b'

It seems I get it, no matter what target type or preset I select.  I tried deinstalling and reinstalling winff/ffmpeg, but to no avail.  Where to go from here?

Dan


> ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jan  4 2012 16:21:50 with gcc 4.6.1
  configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-[NULL @ 0x991d360] Unable to parse option value "1000kb"
Invalid value '1000kb' for option 'b'libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[theora @ 0x991ca20] 7 bits left in packet 82
Input #0, ogg, from '/home/dan/Desktop/vids/2012-01-29-185225.ogv':
  Duration: 01:42:43.16, start: 0.000000, bitrate: 1572 kb/s
    Stream #0.0: Video: theora, yuv420p, 320x240, 30 tbr, 30 tbn, 30 tbc
    Stream #0.1: Audio: vorbis, 44100 Hz, mono, s16, 80 kb/s
[NULL @ 0x991d360] [Eval @ 0xbfdcac8c] Invalid chars 'b' at the end of expression '1000kb'
[NULL @ 0x991d360] Unable to parse option value "1000kb"
Invalid value '1000kb' for option 'b'
Press Enter to Continue


---

### Post by ron999 on 2012-01-29
Hi
You need the later version of presets.xml file.
From here ---> [http://code.google.com/p/winff/downloads/detail?name=presets-libavcodec53-v3.xml.gz]("http://code.google.com/p/winff/downloads/detail?name=presets-libavcodec53-v3.xml.gz")

---

### Post by shortmort37 on 2012-01-30
That did it!  Thanks so much...

---

