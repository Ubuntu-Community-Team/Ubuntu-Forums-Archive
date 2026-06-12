---
title: "AVI Conversion for ARCHOS 18"
date: 2011-01-26
forum: Multimedia Software
---

### Post by keiffee30 on 2011-01-26
I recently purchased an Archos 18 mp3 player 

[**http://www.archos.com/products/mp3_players/archos_18_vision/index.html?country=gb&lang=en**]("http://www.archos.com/products/mp3_players/archos_18_vision/index.html?country=gb&lang=en")

It works like a dream on Ubuntu  except for one detail...to play AVI files on the unit the AVI files first need to be converted to a special AVI format (changes in resolution, frame rate, audio sampling rate, codec, etc). The unit ships with Windows-only AVI converter software creatively called AVIConverter. This software won't work on Wine. I have even downloaded a newer version of AVI Conerter to see if that will work. but nop it dont.

Archos left an example AVI file on the mp3 player.I have seen a app called **"Iriverter"** from the repositories and the app dosen't load up into a GUI. So i tried the command line and typed in this 

**mencoder film to convert.avi -o film to see.avi -ofps 15 -vf-add scale=160:128 -vf-add expand=160:128:-1:-1:1 -srate 44100 -ovc xvid -xvidencopts bitrate=$bitrate:max_bframes=0:quant_type=h263 -oac lavc -lavcopts acodec=mp2:abitrate=96**

When i have tried this there is a conversion so after it finished  (11mins time) i copyed it over to the folder on the Archos18 called "video" i tried to play it and i got really good sound but the film was far too fast and i could see a pic it was jumping all over the place. I have tried some different settings like changing the FPS from 60 down to 10 still can not see a video @ 60 i just get a screen that changed after 10 mins to the next frame, and at 10 see a jumping frame after 1 min of sound the film was already 35 mins into the video? 

Could anyone help out on this ?

---

### Post by ron999 on 2011-01-26
Hi
It would be better if you found more information about the example AVI file.
Use a program such as MediaInfo.
Or even use a command like this:-
```
ffmpeg-i *[COLOR="Red"]filename[/COLOR]*
```

---

### Post by keiffee30 on 2011-01-26
OK no problems i have done a ffmpeg -i and this is the result 

[B]FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:35:47 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, avi, from 'bbb.avi':
  Metadata:
    ISFT            : MEncoder Sherpya-MinGW-20060312-4.1.0
  Duration: 00:09:56.40, start: 0.000000, bitrate: 532 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 160x128 [PAR 1:1 DAR 5:4], PAR 65536:65535 DAR 16384:13107, 15 tbr, 15 tbn, 15 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, 2 channels, s16, 128 kb/s
At least one output file must be specified
[/B]

---

### Post by ron999 on 2011-01-26
OK
Try converting a file using ffmpeg with a command like this:-
```
ffmpeg -i *[COLOR="Red"]filename[/COLOR]* -vcodec mpeg4 -b 500k -s 160x128 -r 15 -acodec mp2 -ar 44100 -ac 2 -ab 128k output.avi
```

---

### Post by keiffee30 on 2011-01-26
i used this and copyed it over to the player, tried playing it and said "wrong file type"

---

### Post by ron999 on 2011-01-26
> **keiffee30 said:**
> ... said "wrong file type"

OK, I've got no more ideas.:(

---

### Post by keiffee30 on 2011-01-26
lol same here. thanks for giving it a go. you got further than i did.

---

### Post by keiffee30 on 2011-04-01
ok i have installed Vbox and installed Windows XP then i installed the program that comes with the playing and enabled the USB this works well and i can convert all the files/videos needed. i know its not a clean fix but more of a work around... and a waste of 7Gb of disk space but its works.

---

