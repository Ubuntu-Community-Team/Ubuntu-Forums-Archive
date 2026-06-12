---
title: "a problem in Winff"
date: 2010-07-22
forum: Multimedia Software
---

### Post by muath on 2010-07-22
[SIZE=3]Hi , [/SIZE][SIZE=3]


when i try to convert a flv video to mp3 by winff

it gets to me this:
[/SIZE][SIZE=3][COLOR=Red]

le-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
.
.
.
Unknown encoder 'libmp3lame'
Press Enter to Continue

[/COLOR][/SIZE][SIZE=3]
- How can i solve this problem? ,
  are there a good video and audio converters?




[/SIZE]

---

### Post by ron999 on 2010-07-22
Hi
WinFF is trying to use **libmp3lame** encoder.
Maybe you haven't got it installed.

You could try converting that video to audio using the command line.
Like this:-

```
ffmpeg -i filename.flv -f mp3 soundtrack.mp3

```

(Use the correct name of your video for 'filename') ;)

---

