---
title: "ffmpeg/ffprobe Bus error (core dumped)"
date: 2020-05-24
forum: Multimedia Software
---

### Post by adenansu on 2020-05-24
Trying to get youtube-dl working, but the root of the issue is ffmpeg/ffprobe.

$ ffmpeg
Bus error (core dumped)


Ubuntu 20.04 LTS

After an apt remove/purge and installing it again:

$ sudo apt install ffmpeg
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  ffmpeg-doc
The following NEW packages will be installed:
  ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,452 kB of archives.
After this operation, 2,054 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/universe amd64 ffmpeg amd64 7:4.2.2-1ubuntu1 [1,452 kB]
Fetched 1,452 kB in 1s (1,634 kB/s)
Selecting previously unselected package ffmpeg.
(Reading database ... 267425 files and directories currently installed.)
Preparing to unpack .../ffmpeg_7%3a4.2.2-1ubuntu1_amd64.deb ...
Unpacking ffmpeg (7:4.2.2-1ubuntu1) ...
Setting up ffmpeg (7:4.2.2-1ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...


I've tried the snap package, aliased ffmpeg.ffprobe to ffprobe, but it can't find any files that I point it to.

$ ffprobe -show_streams ./test.webm
Error: unable to open display
ffprobe version n4.1.4 Copyright (c) 2007-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.4.0-1ubuntu1~18.04.1)
  configuration: --prefix= --prefix=/usr --disable-debug --disable-doc --disable-static --enable-avisynth --enable-cuda --enable-cuvid --enable-libdrm --enabl
e-ffplay --enable-gnutls --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfontconfig --enable-libfreetype --enable-libmp3lame --enable-libopencore
_amrnb --enable-libopencore_amrwb --enable-libopus --enable-libpulse --enable-sdl2 --enable-libspeex --enable-libtheora --enable-libtwolame --enable-libv4l2 -
-enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-libxcb --enable-libxvid --enable-nonfree --enable-nvenc --enable-omx --enable-ope
nal --enable-opencl --enable-runtime-cpudetect --enable-shared --enable-vaapi --enable-vdpau --enable-version3 --enable-xlib
  libavutil      56. 22.100 / 56. 22.100
  libavcodec     58. 35.100 / 58. 35.100
  libavformat    58. 20.100 / 58. 20.100
  libavdevice    58.  5.100 / 58.  5.100
  libavfilter     7. 40.101 /  7. 40.101
  libswscale      5.  3.100 /  5.  3.100
  libswresample   3.  3.100 /  3.  3.100
  libpostproc    55.  3.100 / 55.  3.100
./test.webm: No such file or directory


I went so far as to try to build ffmpeg from source, but it won't build and keeps saying "x265 not found using pkg-config" even though 3.2.1-1build1 is installed (latest version at this moment).

---

### Post by wildmanne39 on 2020-05-24
Hello, we do not allow discussion of youtube-dl here on the forum, please refer to the following link for the reason.

[https://ubuntuforums.org/showthread.php?t=2439118](https://ubuntuforums.org/showthread.php?t=2439118)

Thread Closed.

---

