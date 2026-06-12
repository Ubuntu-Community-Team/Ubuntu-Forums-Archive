---
title: "ffmpeg encode to .mp4 Youtube issue"
date: 2010-08-15
forum: Multimedia Software
---

### Post by LuridCinema on 2010-08-15
I have used the below in ffmpeg to make an .mp4 from an .mov (rendered in cinelerra) for Youtube. It will play fine in VLC on my computer. Usually no issues uploading to youtube, but 1/2 the time youtube does not like the video after youtube processing, the video will not display correctly, it will be blacked out in places and be unusable.

The source video is 24fps 1280x720 .mov ... And result is 1280x720 24fps .mp4

```
ffmpeg -i INPUT.mov -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -wpredp 0 -s 1280x720 -crf 24 -threads 0 OUTPUT.mp4
```

ANY ffmpeg gurus offer any help ? What am I doing wrong here ? Im using a recent ffmpeg build as suggested in the thread "**HOWTO: Install and use the latest FFmpeg and x264"**

My solution has been to take the .mp4 and re-encode to .mpg and upload. The .mpg will be 10 times larger or more. This works but takes a long time to upload.

```
ffmpeg -i INPUT.mp4 -sameq OUTPUT.mpg
```

---

### Post by ron999 on 2010-08-15
Hi
I have recently been converting screencasts for youtube.
I used a very similar command as yours.
Sometimes they were rejected.:(
Sometimes they only played 18 seconds.:(
It fixed it for me by specifying **baseline** profile.:D
Maybe this is what you need too.8)


This was the command that I used successfully:-
```
ffmpeg -i foo -vcodec libx264 -vpre medium -vpre baseline -crf 24 -threads 0 -acodec libfaac -aq 100 foo.mp4
```

Also, you may not need to re-encode the audio channel.
If it's already compressed aac/mp3/vorbis then leave it alone and use **-acodec copy**.

---

### Post by LuridCinema on 2010-08-15
I FORGOT TO MENTION the above .mp4 files load perfectly well onto vimeo...

THANXXX .. I got  an error      "File for preset 'medium' not found" in ffmpeg . I'll see what im missing

---

### Post by ron999 on 2010-08-15
I should have asked you:-
[SIZE="5"][COLOR="Red"]Why not just upload the mov file to YouTube?[/COLOR][/SIZE]:confused:

---

### Post by LuridCinema on 2010-08-15
Because a 7 min .mov file is 17GB !.......... same file in .mp4 is 21mb......... the mpg is 192mb

---

### Post by ron999 on 2010-08-15
> **LuridCinema said:**
> Because a 7 min .mov file is 17GB !.......... same file in .mp4 is 21mb......... 

Yes, I understand.
:redface:

x264 rocks.:guitar:

---

### Post by FakeOutdoorsman on 2010-08-15
Can you show the complete FFmpeg output from this command?
```
ffmpeg -i INPUT.mov
```

> **LuridCinema said:**
> ...
```
ffmpeg -i INPUT.mov -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq [color=#FF0000]-wpredp 0[/color] -s 1280x720 -crf 24 -threads 0 OUTPUT.mp4
```

ANY ffmpeg gurus offer any help ? What am I doing wrong here ? Im using a recent ffmpeg build as suggested in the thread "**HOWTO: Install and use the latest FFmpeg and x264"**
You don't need *-wpredp 0* unless you are hosting your own video and using something like JW Player and your clients are using Adobe Flash Player > 10.1.

> **LuridCinema said:**
> ```
ffmpeg -i INPUT.mp4 -sameq OUTPUT.mpg
```
*-sameq* probably won't work as expected when going from H.264 (I'm guessing this is what your input is) to MPEG-1 video because they use different quantizer scales.  A better option is *-qscale*. A value of *-qscale 2* is roughly visually lossless, and 3-5 is a good balance.  *-sameq* is fine when encoding between these formats: flv, h263, h263+, mpeg1, mpeg2, mpeg4, msmpeg*.

> **ron999 said:**
> ...
Also, you may not need to re-encode the audio channel.
If it's already compressed aac/mp3/vorbis then leave it alone and use **-acodec copy**.

Agreed.  The .mkv container can handle just about anything and YouTube accepts it.

> **LuridCinema said:**
> ...I got  an error      "File for preset 'medium' not found" in ffmpeg . I'll see what im missing
The medium preset is for FFmpeg SVN r22695 (2010-03-26) and above.  Check to see if your FFmpeg is too old.

---

### Post by LuridCinema on 2010-08-16
I updated my ffmpeg mebbe 2 weeks ago. Ill check and redo the build to insure I have the latest & greatest.......

Ok ...output for ffmpeg -i INPUT.mov

```
p9@p9-desktop:/media/STUFF/indie-stuff$ ffmpeg -i indie-intro.mov
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'indie-intro.mov':
  Duration: 00:00:13.60, start: 0.000000, bitrate: 264390 kb/s
    Stream #0.0(eng): Video: rawvideo, yuv420p, 1280x720, 24 tbr, 24 tbn, 24 tbc
    Stream #0.1(eng): Audio: mp3, 48000 Hz, stereo, s16
At least one output file must be specified
```

---

### Post by FakeOutdoorsman on 2010-08-16
> **LuridCinema said:**
> I updated my ffmpeg mebbe 2 weeks ago. Ill check and redo the build to insure I have the latest & greatest.......

Ok ...output for ffmpeg -i INPUT.mov

```
p9@p9-desktop:/media/STUFF/indie-stuff$ ffmpeg -i indie-intro.mov
[color=#FF0000]FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1[/color], Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'indie-intro.mov':
  Duration: 00:00:13.60, start: 0.000000, bitrate: 264390 kb/s
    Stream #0.0(eng): Video: rawvideo, yuv420p, 1280x720, 24 tbr, 24 tbn, 24 tbc
    Stream #0.1(eng): Audio: mp3, 48000 Hz, stereo, s16
At least one output file must be specified
```

Looks like you have the repository version of FFmpeg installed.  If you require both you can have both the repository version and a compiled FFmpeg on the same system.  Just follow this guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

[list][*] Don't remove *ffmpeg* as shown in step 1.
[*] Change *--pkgname=x264* to *--pkgname=x264-git* in step 3.
[*] Change *--pkgname=ffmpeg* to *--pkgname=ffmpeg-svn* in step 6.[/list]

Now the compiled ffmpeg in */usr/local/bin* will take priority over the repository ffmpeg in */usr/bin* when using the command-line, but other programs that want the repository ffmpeg might work too.

Or you can simply continue to use the repository FFmpeg if you want.  Just change *-vpre medium* to *default*, *normal* or *hq*.

---

### Post by LuridCinema on 2010-08-16
OK fine... Thanxxx, I'll give it a try

---

