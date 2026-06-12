---
title: "ffmpeg (simple convertion does not work)"
date: 2012-04-25
forum: Multimedia Software
---

### Post by 1885 on 2012-04-25
root@io:~# uname -a
Linux io 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux
root@io:~# 
I'm running xubuntu on a laptop

Here is my error:

```
root@io:/home/cwc/Desktop# ffmpeg -i 100_6039.mov ns1.mp4
ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jan  4 2012 16:21:50 with gcc 4.6.1
  configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.3ubuntu0.11.10.1+medibuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1+medibuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0

Seems stream 0 codec frame rate differs from container frame rate: 100.00 (100/1) -> 12.60 (1320000/104771)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '100_6039.mov':
  Metadata:
    creation_time   : 2008-08-11 13:53:22
    comment         : EASTMAN KODAK COMPANY  KODAK LS753 ZOOM DIGITAL CAMERA
    comment-eng     : EASTMAN KODAK COMPANY  KODAK LS753 ZOOM DIGITAL CAMERA
  Duration: 00:00:13.09, start: 0.000000, bitrate: 2274 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 2145 kb/s, 12.60 fps, 12.60 tbr, 2640k tbn, 100 tbc
    Metadata:
      creation_time   : 2008-08-11 13:53:22
    Stream #0.1(eng): Audio: pcm_mulaw, 16000 Hz, 1 channels, s16, 128 kb/s
    Metadata:
      creation_time   : 2008-08-11 13:53:22
[buffer @ 0x8b94c40] w:640 h:480 pixfmt:yuv420p
[mpeg4 @ 0x8b917c0] timebase 104771/1320000 not supported by MPEG 4 standard, the maximum admitted value for the timebase denominator is 65535
Output #0, mp4, to 'ns1.mp4':
    Stream #0.0(eng): Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 12.60 tbc
    Metadata:
      creation_time   : 2008-08-11 13:53:22
    Stream #0.1(eng): Audio: libfaac, 16000 Hz, 1 channels, s16, 64 kb/s
    Metadata:
      creation_time   : 2008-08-11 13:53:22
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

---

### Post by Jose Catre-Vandis on 2012-04-25
Looks like there is a problem with the timecode on the mov file.

Assume the mov file plays back OK with mplayer?

Try:
```
ffmpeg -i input.mov output.avi
```maybe this will work?

---

### Post by 1885 on 2012-04-25
> **Jose Catre-Vandis said:**
> Looks like there is a problem with the timecode on the mov file.

Assume the mov file plays back OK with mplayer?

Try:
```
ffmpeg -i input.mov output.avi
```maybe this will work?

same error :(  
thanks for the line!

---

### Post by Yellow Pasque on 2012-04-25
It looks like you have mixed ffmpeg/libav packages from Ubuntu and medibuntu. That might be part of the issue.

---

### Post by 1885 on 2012-04-25
> **Temüjin said:**
> It looks like you have mixed ffmpeg/libav packages from Ubuntu and medibuntu. That might be part of the issue.


yes i thought medibuntu would help.  how do i remove the medibuntu packages?

---

### Post by FakeOutdoorsman on 2012-04-25
Try adding *-r 12.6* as an output option (after *-i input.mov*) to your original command. If that works consider also adding *-qscale* with a value between 2-5 to increase quality of the output (the default setting is usually crappy). A lower value is higher quality.

**Edit:** Would you be willing to provide this file as a sample? I'd be interested how recent FFmpeg deals with it.
 
> **Temüjin said:**
> It looks like you have mixed ffmpeg/libav packages from Ubuntu and medibuntu. That might be part of the issue.
That's the normal output when the "lib*-extra-5*" Medibuntu packages are used and can be ignored although it doesn't look very good.

---

### Post by BicyclerBoy on 2012-04-25
Your error suggests the mpeg4 container does not support the output frame rate specified with the fractional ratio (your Kodak camera produces).

You can try simple step of adding (after the -i) -r 25 or -r 29.97..

ffmpeg's frame rate conversion is not good..they will not/can not implement frame weighted creation/interpolation..  

A better rate conversion is to use:
- ffmpeg to  convert inputfile --> outfile-rawvideo.yuv (-vcodec rawvideo -pix_fmt yuv420p) 
- yuvfps -w or yuvmotionfps to convert to required output fps.
- ffmpeg to convert raw yuv back to video container/codec.

yuvfps is part of mjpegtools
yuvmotionfps:
[http://jcornet.free.fr/linux/yuvmotionfps.html](http://jcornet.free.fr/linux/yuvmotionfps.html)

This ffmpeg ppa seems complete & is not as old as medibuntu.
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

---

### Post by 1885 on 2012-04-25
thank you so much for the help!

this line did the trick!

cwc@io:~/Desktop$ ffmpeg -i 100_6039.mov -r 12.6 -qscale 5 rtest2.mp4

---

### Post by FakeOutdoorsman on 2012-04-25
12.6 seems like an odd value, but it's what ffmpeg came up with although I doubt that's the actual frame rate. A more normal value is probably *-r 25* or *-r 29.97* (depending on your region), as BicyclerBoy mentioned, or slightly more accurate is *-r ntsc* or *-r 30000/1001* instead of 29.97. ffmpeg will either simply drop or duplicate frames when converting between frame rates.

---

### Post by 1885 on 2012-04-26
> **BicyclerBoy said:**
> Your error suggests the mpeg4 container does not support the output frame rate specified with the fractional ratio (your Kodak camera produces).

You can try simple step of adding (after the -i) -r 25 or -r 29.97..

ffmpeg's frame rate conversion is not good..they will not/can not implement frame weighted creation/interpolation..  

A better rate conversion is to use:
- ffmpeg to  convert inputfile --> outfile-rawvideo.yuv (-vcodec rawvideo -pix_fmt yuv420p) 
- yuvfps -w or yuvmotionfps to convert to required output fps.
- ffmpeg to convert raw yuv back to video container/codec.

yuvfps is part of mjpegtools
yuvmotionfps:
[http://jcornet.free.fr/linux/yuvmotionfps.html](http://jcornet.free.fr/linux/yuvmotionfps.html)

This ffmpeg ppa seems complete & is not as old as medibuntu.
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg]("https://launchpad.net/%7Ejon-severinsson/+archive/ffmpeg")

thank you so much for the lines!   this is epic!

---

