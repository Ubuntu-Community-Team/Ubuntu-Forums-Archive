---
title: "ffmpeg video capture"
date: 2010-08-30
forum: Multimedia Software
---

### Post by mike4ubuntu on 2010-08-30
Anybody had any success in getting ffmpeg to work as advertised with video capture from a webcam?  I really want to convert the webcam output to VP8 or H264, but apparently ffmpeg can't even capture the webcam with a video4linux device.

```
mike@lic9:/opt/test/vp8$ ffmpeg -f oss -i /dev/dsp -f video4linux2 -i /dev/video0 test.mpg
FFmpeg version SVN-r23439, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun  3 2010 11:01:08 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --
enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-lib
vorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.16. 0 / 50.16. 0
  libavcodec    52.73. 0 / 52.73. 0
  libavformat   52.67. 0 / 52.67. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[oss @ 0x9c1f510]Estimating duration from bitrate, this may be inaccurate
Input #0, oss, from '/dev/dsp':
  Duration: N/A, start: 1283203006.144882, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s
[video4linux2 @ 0x9c21aa0]Cannot find a proper format for codec_id 0, pix_fmt -1.
/dev/video0: Input/output error
```

---

### Post by mike4ubuntu on 2010-08-31
I logged onto another machine that is running 64bit Lucid.  It's a different error, but it seems like it may get farther.  I checked v4l-info to get the proper size the webcam uses by default 640x480.

```
$ sudo ffmpeg -f video4linux2 -i /dev/video0 -s 640x480 -r 60000/10010 out.mpeg
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau
--enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable
-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --
enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
[video4linux2 @ 0x1282480]Wrong size (0x0)
/dev/video0: Error while opening file
```

I actually intended to get the medibuntu version of ffmpeg, but I think I actually have the normal Ubuntu repository version.

```

mike@lic8:/opt/test/vp8$ sudo apt-cache show ffmpeg
Package: ffmpeg
Priority: optional
Section: graphics
Installed-Size: 792
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 4:0.5.1-1ubuntu1
Depends: libavcodec52 (>= 4:0.5.1-1ubuntu1) | libavcodec-extra-52 (>= 4:0.5.1-1ubuntu1), libavcodec52 (<< 4:0.5.1-99) |
libavcodec-extra-52 (<< 4:0.5.1-99), libavdevice52 (>= 4:0.5.1-1ubuntu1) | libavdevice-extra-52 (>= 4:0.5.1-1ubuntu1), l
ibavdevice52 (<< 4:0.5.1-99) | libavdevice-extra-52 (<< 4:0.5.1-99), libavfilter0 (>= 4:0.5.1-1ubuntu1) | libavfilter-ex
tra-0 (>= 4:0.5.1-1ubuntu1), libavfilter0 (<< 4:0.5.1-99) | libavfilter-extra-0 (<< 4:0.5.1-99), libavformat52 (>= 4:0.5
.1-1ubuntu1) | libavformat-extra-52 (>= 4:0.5.1-1ubuntu1), libavformat52 (<< 4:0.5.1-99) | libavformat-extra-52 (<< 4:0.
5.1-99), libavutil49 (>= 4:0.5.1-1ubuntu1) | libavutil-extra-49 (>= 4:0.5.1-1ubuntu1), libavutil49 (<< 4:0.5.1-99) | lib
avutil-extra-49 (<< 4:0.5.1-99), libc6 (>= 2.7), libpostproc51 (>= 4:0.5.1-1ubuntu1) | libpostproc-extra-51 (>= 4:0.5.1-
1ubuntu1), libpostproc51 (<< 4:0.5.1-99) | libpostproc-extra-51 (<< 4:0.5.1-99), libsdl1.2debian (>= 1.2.10-1), libswsca
le0 (>= 4:0.5.1-1ubuntu1) | libswscale-extra-0 (>= 4:0.5.1-1ubuntu1), libswscale0 (<< 4:0.5.1-99) | libswscale-extra-0 (
<< 4:0.5.1-99)
Filename: pool/main/f/ffmpeg/ffmpeg_0.5.1-1ubuntu1_amd64.deb
Size: 242256
MD5sum: 64198ad1625452a353fc7b12dd660a12
SHA1: 0a680590ed9d5b64d31d7fa11514448d5f138f7e
SHA256: e4c54c86cc1c7376715b07e471e2a0c475bb46eb94c26175dfcd09c65fa74912
Description: multimedia player, server and encoder
 This package contains the ffplay multimedia player, the ffserver streaming
 server and the ffmpeg audio and video encoder. They support most existing
 file formats (AVI, MPEG, OGG, Matroska, ASF...) and encoding formats (MPEG,
 DivX, MPEG4, AC3, DV...).
Homepage: http://ffmpeg.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend

```

---

### Post by FakeOutdoorsman on 2010-08-31
> **mike4ubuntu said:**
> I logged onto another machine that is running 64bit Lucid.  It's a different error, but it seems like it may get farther.  I checked v4l-info to get the proper size the webcam uses by default 640x480.

```
$ sudo ffmpeg -f video4linux2 -i /dev/video0 -s 640x480 -r 60000/10010 out.mpeg
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau
--enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable
-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --
enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
[video4linux2 @ 0x1282480]Wrong size (0x0)
/dev/video0: Error while opening file
```

Do you really need the sudo?  Your -s and -r options are being applied to the output.  Try moving them before the -i to make them apply to the input:
```
ffmpeg -f video4linux2 -s 640x480 -r ntsc -i /dev/video0 -qscale 3 out.mpeg
```
Also, did you mean *60000/1001* for a frame rate? I used *ntsc* in my example and added *-qscale 4* to the output for constant quality mode.

---

### Post by mike4ubuntu on 2010-09-02
yep, that worked, thanks.  Ran through several of the output containers with different a/v codecs and it all seemed to work just fine.  Is there a way to actually specify two different audio input devices and have ffmpeg mix the two inputs to the two channels of the output?

---

### Post by FakeOutdoorsman on 2010-09-02
> **mike4ubuntu said:**
> Is there a way to actually specify two different audio input devices and have ffmpeg mix the two inputs to the two channels of the output?

I don't know. Never tried it myself.  Try asking at the *#ffmpeg* IRC channel or the ffmpeg-user mailing list.

---

### Post by shantiq on 2010-09-27
> **FakeOutdoorsman said:**
> 
```
ffmpeg -f video4linux2 -s 640x480 -r ntsc -i /dev/video0 -qscale 3 out.mpeg
```
.


this works well but no sound on replay i use an alpha lexicon external soundcard system wide

could that be the problem here?

---

### Post by mike4ubuntu on 2010-10-01
you need to specify the sound input as well

```
ffmpeg -t 00:00:30  -f video4linux2 -s 640x480 -r ntsc -i /dev/video0 -f alsa -ac 2 -i pulse -qscale 3 video-with-sound.avi

```

---

### Post by shantiq on 2010-10-01
> **mike4ubuntu said:**
> you need to specify the sound input as well

```
ffmpeg -t 00:00:30  -f video4linux2 -s 640x480 -r ntsc -i /dev/video0 -f alsa -ac 2 -i pulse -qscale 3 video-with-sound.avi

```




works a charm  


this also

```

ffmpeg -f alsa -ac 2 -i pulse  -f video4linux2 -i /dev/video0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -s 320x240   -r 30  -y  ./Desktop/mywebcam.avi
```



   worked out a few more tricks [here]("http://ubuntuforums.org/showthread.php?t=1585928") just for microphone you might want  perhaps

---

### Post by tagnu on 2010-11-02
Hi,   When I try the following command with my usb webcam: 
 ```
ffmpeg  -f video4linux2 -s 352x288 -r ntsc -i /dev/video0 -qscale 3 video.avi
```   I get. 
 ```
..   
..     
bpostproc   51. 2. 0 / 51. 2. 0   built on Mar  4 2010 12:35:30, gcc: 4.4.3   
[video4linux2 @ 0x826aa60][3]Capabilities: 5000001   
[video4linux2 @ 0x826aa60]Cannot find a proper format.   
/dev/video0: I/O error occurred   
Usually that means that input file is truncated and/or corrupted. 
```I'm able to view the webcam video using **gstreamer-properties** with default pipeline   ```
 v4l2src device="/dev/video0"
```Any idea?   

Thank you.       

> **FakeOutdoorsman said:**
> Do you really need the sudo?  Your -s and -r options are being applied to the output.  Try moving them before the -i to make them apply to the input:
```
ffmpeg -f video4linux2 -s 640x480 -r ntsc -i /dev/video0 -qscale 3 out.mpeg
```Also, did you mean *60000/1001* for a frame rate? I used *ntsc* in my example and added *-qscale 4* to the output for constant quality mode.

---

### Post by mike4ubuntu on 2010-11-02
not sure.  That command you had...

```
ffmpeg  -f video4linux2 -s 352x288 -r ntsc -i /dev/video0 -qscale 3 video.avi
```

worked just fine with my Phillips webcam connected to /dev/video0.

---

### Post by tagnu on 2010-11-03
I tried it on another pc (laptop with webcam) and it works perfectly.  May be it has something to do with my usb webcam.

---

