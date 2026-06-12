---
title: "Can't use my kinect 2 for skype and zoom but it works with ffmpeg"
date: 2022-01-22
forum: Multimedia Software
---

### Post by marietto2008 on 2022-01-22
Hello Ubuntu lovers,

I have compiled and loaded the kernel driver module "gspca-kinect2" on the github below because I wanted that my kinect 2 was detected as webcam for skype,but it did not work. The commands that I have issued are explained here :

[https://github.com/tduck973564/gspca-kinect2](https://github.com/tduck973564/gspca-kinect2)

To recap :
```

$ wget -q -O - https://github.com/.../gspca.../raw/master/install-webcam.sh | sudo sh
$ make -C /lib/modules/`uname -r`/build  M=`pwd` SRCROOT=`pwd` clean modules  
$ sudo /sbin/rmmod gspca_main
$ sudo /sbin/modprobe videodev
$ sudo /sbin/insmod ./gspca_main.ko  
$ sudo /sbin/insmod ./gspca_kinect2.ko  
$ ffmpeg  -framerate 30 -video_size 640x480 -i /dev/video1  test.avi  
$ mplayer test.avi
```

and it worked (it means that it has been able to capture what's inside my room and it saved it on the avi file that I have been able to reproduce :

```
# ffmpeg  -framerate 30 -video_size 640x480 -i /dev/video1 test.avi

ffmpeg version 4.4-6ubuntu5 Copyright (c) 2000-2021 the FFmpeg developers
  built with gcc 11 (Ubuntu 11.2.0-7ubuntu1)
  configuration: --prefix=/usr --extra-version=6ubuntu5 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-nvenc --enable-chromaprint --enable-frei0r --enable-libx264 --enable-shared
  libavutil      56. 70.100 / 56. 70.100
  libavcodec     58.134.100 / 58.134.100
  libavformat    58. 76.100 / 58. 76.100
  libavdevice    58. 13.100 / 58. 13.100
  libavfilter     7.110.100 /  7.110.100
  libswscale      5.  9.100 /  5.  9.100
  libswresample   3.  9.100 /  3.  9.100
  libpostproc    55.  9.100 / 55.  9.100
[video4linux2,v4l2 @ 0x55dd58ce0400] The V4L2 driver changed the video from 640x480 to 1920x1080
[video4linux2,v4l2 @ 0x55dd58ce0400] The driver does not permit changing the time per frame
[video4linux2,v4l2 @ 0x55dd58ce0400] Time per frame unknown
Input #0, video4linux2,v4l2, from '/dev/video1':
  Duration: N/A, start: 4818.621738, bitrate: N/A
  Stream #0:0: Video: mjpeg (Baseline), yuvj422p(pc, bt470bg/unknown/unknown), 1920x1080, 15 tbr, 1000k tbn, 1000k tbc
Stream mapping:
  Stream #0:0 -> #0:0 (mjpeg (native) -> mpeg4 (native))
Press [q] to stop, [?] for help
[swscaler @ 0x55dd58e25fc0] deprecated pixel format used, make sure you did set range correctly
Output #0, avi, to 'test.avi':
  Metadata:
    ISFT            : Lavf58.76.100
  Stream #0:0: Video: mpeg4 (FMP4 / 0x34504D46), yuv420p(tv, bt470bg/unknown/unknown, progressive), 1920x1080, q=2-31, 200 kb/s, 15 fps, 15 tbn
    Metadata:
      encoder         : Lavc58.134.100 mpeg4
    Side data:
      cpb: bitrate max/min/avg: 0/0/200000 buffer size: 0 vbv_delay: N/A
frame=   74 fps= 16 q=31.0 Lsize=     866kB time=00:00:05.93 bitrate=1196.1kbits/s speed=1.28x       
video:859kB audio:0kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.894046%
Exiting normally, received signal 2.
```

Problem arises when I tried to use the device /dev/video1 for skype and for zoom. Infact for some unknown reason,they haven't been able to detect correctly the kinect 2 and I saw only a black screen instead of my face. Below you can see what's the device that they have detected (they = skype for web + chrome browser and zoom ; instead the skype client on ubuntu detects only a dummy device located at 0000:0000) :

[https://ibb.co/6YcFLZd](https://ibb.co/6YcFLZd)

My kinect 2 on ubuntu 21.10 is located at the address below :

**Bus 004 Device 002: ID 045e:02c4 Microsoft Corp. Xbox NUI Sensor.**

---

