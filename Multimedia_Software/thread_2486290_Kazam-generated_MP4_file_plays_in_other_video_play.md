---
title: "Kazam-generated MP4 file plays in other video players, but not VLC"
date: 2023-04-25
forum: Multimedia Software
---

### Post by raphaell2 on 2023-04-25
Hi everyone, 

I'm sometimes using kazam to do screen captures, with the video set to h264 (mp4). My files from that source play in some other video players, such as Celluloid, but in vlc, only the audio plays. The video doesn't show. Is there some way to use ffmpeg to convert my files to a slightly different mp4 format that vly will play?

Here's the ffprobe result for my latest file:

ffprobe version 5.1.1-1ubuntu2.1 Copyright (c) 2007-2022 the FFmpeg developers
  built with gcc 12 (Ubuntu 12.2.0-3ubuntu1)
  configuration: --prefix=/usr --extra-version=1ubuntu2.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libglslang --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librist --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libsvtav1 --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --disable-sndio --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-libplacebo --enable-shared
  libavutil      57. 28.100 / 57. 28.100
  libavcodec     59. 37.100 / 59. 37.100
  libavformat    59. 27.100 / 59. 27.100
  libavdevice    59.  7.100 / 59.  7.100
  libavfilter     8. 44.100 /  8. 44.100
  libswscale      6.  7.100 /  6.  7.100
  libswresample   4.  7.100 /  4.  7.100
  libpostproc    56.  6.100 / 56.  6.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Screencast 2023-04-25 10:48:49.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42mp41isomiso2
    creation_time   : 2023-04-25T08:24:10.000000Z
    encoder         : x264
  Duration: 00:23:47.20, start: 0.000000, bitrate: 12551 kb/s
  Stream #0:0[0x1](und): Video: h264 (High 4:4:4 Predictive) (avc1 / 0x31637661), yuv444p(tv, bt709, progressive), 1920x1080 [SAR 1:1 DAR 16:9], 12425 kb/s, 30 fps, 30 tbr, 3k tbn (default)
    Metadata:
      creation_time   : 2023-04-25T08:24:10.000000Z
      handler_name    : VideoHandler
      vendor_id       : [0][0][0][0]
  Stream #0:1[0x2](und): Audio: mp3 (mp4a / 0x6134706D), 44100 Hz, mono, fltp, 124 kb/s (default)
    Metadata:
      creation_time   : 2023-04-25T08:24:10.000000Z
      handler_name    : SoundHandler
      vendor_id       : [0][0][0][0]


Thank you in advance!

---

### Post by #&amp;thj^% on 2023-04-25
Your KAZAM video features YUV444P pixel format which some players may not support without extra filters. Using ffmpeg.
I've used ffmpeg to convert to a player friendly video. For this you will need to (replace input_file.mp4 and output_file.mp4):
```
ffmpeg -y -i input_file.mp4 -c:v libx264 -c:a aac -strict experimental -tune fastdecode -pix_fmt yuv420p -b:a 192k -ar 48000 output_file.mp4
```
Or:
```
ffmpeg -i in.mp4 -pix_fmt yuv420p -c:a copy -movflags +faststart out.mp4
```
Not as good of quality though, and you may have to tweak those to fit your preference.(But give it a shot)
Also more info found here: [https://ffmpeg.org/ffmpeg-devices.html#video4linux2_002c-v4l2](https://ffmpeg.org/ffmpeg-devices.html#video4linux2_002c-v4l2)
For Quality sample I've included a screenshot. (for the second command)

---

### Post by raphaell2 on 2023-04-25
Thank you, your first command did the trick!

---

### Post by #&amp;thj^% on 2023-04-25
:)

---

### Post by monkeybrain20122 on 2023-04-25
Well how do you install kazam? I think the copy in the repo is broken.

get it from from [https://github.com/niknah/kazam](https://github.com/niknah/kazam)

and run it locally (cd into the bin and run ./run_local_dev.sh, of course you can edit the .desktop file in the data folder)

It works perfectly on 22.04

P.S. I check my notes and there are some workarounds which may or may not be needed
sudo apt-get install libkeybinder-3.0-0 gir1.2-keybinder to fix "ValueError: Namespace Keybinder not available"

Reinstall gstreamer1.0-pulseaudio and/or gstreamer1.0-gl to fixe Gst.ElementFactory.make() return none or 'NoneType' object has no attribute

---

### Post by monkeybrain20122 on 2023-04-25
deleted. duplicated.

---

