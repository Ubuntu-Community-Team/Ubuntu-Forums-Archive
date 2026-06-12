---
title: "Memory stick stopped working when copying files"
date: 2014-12-26
forum: Multimedia Software
---

### Post by mpietron on 2014-12-26
Hello,
I cut (Ctrl+x) the files from SD Card (GoPro mp4 files) to memory sitck.  When files is coping the memory stick stopped working :(
I saw on my SD card only empty directorys without any file. I recovered files from SD. Images are OK but mp4 are corrupted (no sound, no picture but i can select any moment of movie - timeline is active).

ffmpeg details abut file:
```

sudo ffmpeg -i f1397760.mp4
ffmpeg version 1.2.6-7:1.2.6-1~trusty1 Copyright (c) 2000-2014 the FFmpeg developers
  built on Apr 26 2014 18:52:58 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --arch=amd64 --disable-stripping --enable-avresample --enable-pthreads --enable-runtime-cpudetect --extra-version='7:1.2.6-1~trusty1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  libavutil      52. 18.100 / 52. 18.100
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.104 / 54. 63.104
  libavdevice    53.  5.103 / 53.  5.103
  libavfilter     3. 42.103 /  3. 42.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[h264 @ 0xf7fec0] AVC: nal size -1346660820
[h264 @ 0xf7fec0] no frame!
[aac @ 0xf64ca0] channel element 3.3 is not allocated
[h264 @ 0xf7fec0] AVC: nal size 1951024004
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1758541168
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1055464807
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -94515656
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 351981851
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1518245683
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1083110067
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -1648367802
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1120343617
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 352752473
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -1102288219
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 969501450
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 284596044
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -739792764
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -1444838979
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -1272870936
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -558264499
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -1878490405
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1523859182
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1548594500
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -978675836
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -1363826949
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1389899894
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1838580007
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -902426904
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1399805711
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1983856854
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -1732720869
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 91973171
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 523852218
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 295755524
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1271810169
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 991975244
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -684971875
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -982463281
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 138246999
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 2117554925
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 781657161
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 561064849
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 689180408
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 353335364
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1455240355
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -982052793
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 780333910
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -678349544
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 92628203
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -141765741
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -677466235
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -1774044577
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -754694766
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size -1647501761
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 359179800
[h264 @ 0xf7fec0] no frame!
[h264 @ 0xf7fec0] AVC: nal size 1146354327
[h264 @ 0xf7fec0] no frame!
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xf7f2c0] decoding for stream 0 failed
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xf7f2c0] Could not find codec parameters for stream 0 (Video: h264 (avc1 / 0x31637661), 1920x1080, 20069 kb/s): unspecified pixel format
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'f1397760.mp4':
  Metadata:
    major_brand     : avc1
    minor_version   : 0
    compatible_brands: avc1isom
    creation_time   : 2014-09-08 08:52:31
  Duration: 00:00:32.90, start: 0.000000, bitrate: 20404 kb/s
    Stream #0:0(eng): Video: h264 (avc1 / 0x31637661), 1920x1080, 20069 kb/s, 29.97 fps, 29.97 tbr, 180k tbn, 360k tbc
    Metadata:
      creation_time   : 2014-09-08 08:52:31
      handler_name    :  GoPro AVC
    Stream #0:1(eng): Audio: aac (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 128 kb/s
    Metadata:
      creation_time   : 2014-09-08 08:52:31
      handler_name    :  GoPro AA

```
Any suggestions? The files is important for me.

---

### Post by Jonor on 2014-12-30
How was the recovery made ?
Maybe try using testdisk to make a more successful recovery - warning: not tried to do this myself though.

---

### Post by sudodus on 2015-01-01
Photorec is an alternative, if testdisk does not work.

But I repeat the question by *Jonor*. Please tell us more about what you have done so far. Otherwise we can only guess instead of giving good advice.

---

### Post by coldraven on 2015-01-01
Can you undelete the file in the GoPro? If you have not used it since your aborted cut and paste the file should still be there.
I just googled "undelete gopro video" and there seems to be many answers.

---

