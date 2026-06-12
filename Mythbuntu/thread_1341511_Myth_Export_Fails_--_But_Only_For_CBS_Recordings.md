---
title: "Myth Export Fails -- But Only For CBS Recordings"
date: 2009-11-29
forum: Mythbuntu
---

### Post by MooseMooseMoose on 2009-11-29
I'm having some problems getting mythexport to transcode recordings from CBS for an iphone (or any other type of device as far as I can tell).  Essentially, mythexport will work for recordings from any of the other channels, but craps out if I try do one from CBS.

I have looked in the mythexport.log, and then tried to run the ffmpeg command from there that spits out the error.

```
nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1021_20091129174000.mpg -y -acodec libmp3lame -ab 96kb -vcodec mpeg4 -b 600kb -mbd rd -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 -pass 1/2 -s 240x320 -aspect 4:3 '/var/lib/mythtv/mythexport/WCBS-HD-2_1_WCBS_HD_-Sun_Nov_29_17_40_00_2009-2009112917400.mp4'
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mpegts, from '/var/lib/mythtv/recordings/1021_20091129174000.mpg':
  Duration: 00:02:43.26, start: 40274.800933, bitrate: 14038 kb/s
  Program 1 
    Stream #0.0[0x31]: Video: mpeg2video, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 17067 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x34](eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0x35](spa): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
Output #0, mp4, to '/var/lib/mythtv/mythexport/WCBS-HD-2_1_WCBS_HD_-Sun_Nov_29_17_40_00_2009-2009112917400.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 240x320 [PAR 16:9 DAR 4:3], q=2-31, pass 1, 600 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1(eng): Audio: libmp3lame, 0 channels, s16, 96 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mp4 @ 0x902be30]sample rate not set
Could not write header for output file #0 (incorrect codec parameters ?)

```Looking through this I see two possible candidates for the error: (1) the mismatch between the framerate and the container rate and (2) the inability to write header for the output file at the end.  

The mythexport directory is a samba share, but I think I've mounted it as appropriately permissioned (777).  I also tried running with the line mounting it in my fstab commented out, so it should all be local, but that doesn't make a difference.  I also tried modifying the command to dump the file in my directory (run as me) with the same results

```

nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1021_20091129174000.mpg -y -acodec libmp3lame -ab 128kb -vcodec mpeg4 -b 500kb -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 480x320 -ac 2 -aspect 16:9 '~/WCBS-HD-2_1_WCBS_HD_-Sun_Nov_29_17_40_00_2009-2009112917400.mp4'
```I've tried googling without success for these errors.  Any help, pointers or suggestions would be quite welcome.  Thanks.

---

### Post by MooseMooseMoose on 2009-12-12
In case anyone else is having issues with this and comes upon this post looking for an answer.  Adding 

```
-ar 44100
```

to the command line makes it work.  You can edit /etc/mythtv/mythexport/mythexport_settings.cfg to add that and it appears to work now.

---

