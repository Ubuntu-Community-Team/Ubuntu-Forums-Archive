---
title: "ffmpeg stripped too much (-fpre not available)"
date: 2011-05-15
forum: Multimedia Software
---

### Post by hemertje on 2011-05-15
Hi all,

new to this forum, hope you can help me out.
I'm using latest Ubuntu 64 bits version.

Last januari my son was born, made HD recording with my HD JVC camcorder,
This recorder is producing MTS files, which now i want to convert to H264, see the commandline below:

```

hemertje@hemertje-laptop:~/video$ ffmpeg -fpre /tmp/ffmpeg.preset -strict experimental -vsync 1 -async 10000 -i "20110419 - lekker spelen.MTS" -vcodec libx264 -crf 24 -acodec aac -ac 2 -ar 48000 -ab 128k -f mp4 "20110419 - lekker spelen.MTS_MP4" 
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al. 
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static 
  libavutil    49.15. 0 / 49.15. 0 
  libavcodec    52.20. 1 / 52.20. 1 
  libavformat   52.31. 0 / 52.31. 0 
  libavdevice   52. 1. 0 / 52. 1. 0 
  libavfilter    0. 4. 0 /  0. 4. 0 
  libswscale    0. 7. 1 /  0. 7. 1 
  libpostproc   51. 2. 0 / 51. 2. 0 
  built on Mar 31 2011 18:59:37, gcc: 4.4.3 
ffmpeg: unrecognized option '-fpre' 
hemertje@hemertje-laptop:~/video$ ffmpeg -help | less 
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al. 
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static 
  libavutil    49.15. 0 / 49.15. 0 
  libavcodec    52.20. 1 / 52.20. 1 
  libavformat   52.31. 0 / 52.31. 0 
  libavdevice   52. 1. 0 / 52. 1. 0 
  libavfilter    0. 4. 0 /  0. 4. 0 
  libswscale    0. 7. 1 /  0. 7. 1 
  libpostproc   51. 2. 0 / 51. 2. 0 
  built on Mar 31 2011 18:59:37, gcc: 4.4.3 
ffmpeg: missing argument for option '-help' 
 
[1]+  Stopped              ffmpeg -help | less 
hemertje@hemertje-laptop:~/video$ 
```seems that ffmpeg is stripped too much.

Can someone help me out to convert my MTS files into H264?

Thanks!

Greetings, hemertje

---

### Post by ajgreeny on 2011-05-15
You probably need to install the various **libav*-extra-**** packages.  There are at least 5 of them that I always add in Lucid, there may be others available as well so search for them:-

libavcodec-extra-52
libavdevice-extra-52
libavfilter-extra-1
libavformat-extra-52
libavutil-extra-50

I don't know if all are needed for that filetype, but I'm pretty sure that with them you will enable to encode as you want.  The numbers at the end may be different depending on your Ubuntu version, and in the past these packages were known as "unstripped".  They are all in the medibuntu multiverse repos.

PS:  I'm not sure about the **ffmpeg -fpre** at the start of your command;  what should that do?

---

### Post by andrew.46 on 2011-05-16
Hmmm.... is that the repository version of FFmpeg or have you picked it up elsewhere? BTW congrats on the birth of your son :).

---

### Post by hemertje on 2011-05-16
> **ajgreeny said:**
> You probably need to install the various **libav*-extra-**** packages.  There are at least 5 of them that I always add in Lucid, there may be others available as well so search for them:-

libavcodec-extra-52
libavdevice-extra-52
libavfilter-extra-1
libavformat-extra-52
libavutil-extra-50

I don't know if all are needed for that filetype, but I'm pretty sure that with them you will enable to encode as you want.  The numbers at the end may be different depending on your Ubuntu version, and in the past these packages were known as "unstripped".  They are all in the medibuntu multiverse repos.

PS:  I'm not sure about the **ffmpeg -fpre** at the start of your command;  what should that do?

tried it, still no go with the -fpre option

also tried the [http://gebaar.blogspot.com/2009/06/howto-easily-enable-mp3-mpeg4-aac-and.html](http://gebaar.blogspot.com/2009/06/howto-easily-enable-mp3-mpeg4-aac-and.html) option

[FONT=Verdana]Installing the "unstripped" libraries from the repository
This  is the easiest option for Intrepid and Jaunty users and is not  available for prior Ubuntu versions. FFmpeg from the repository does not  include many restricted encoders, formats, and codecs including: h261,  h263, h263p, aac (libfaac), mp3 (libmp3lame), h264 (libx264), xvid  (libxvid), mpeg2video, mpeg4, msmpeg4, msmpeg4v1, and msmpeg4v2. You can  fix this by installing the "unstripped" FFmpeg libraries that will  enable these restricted encoders.

but also still no go...


[/FONT]

---

### Post by hemertje on 2011-05-16
> **ajgreeny said:**
> PS:  I'm not sure about the **ffmpeg -fpre** at the start of your command;  what should that do?

with -fpre (i believe in fedora) you can use a presetfile for the encoding like a file that ends at .ffpreset, for example /tmp/ffmpeg.preset

```
coder=1
flags=+loop
flags2=+wpred+mixed_refs+fastpskip+aud+dct8x8+bpyramid+mbtree
partitions=parti4x4+parti8x8+partp4x4+partp8x8+partb8x8
cmp=+chroma
me_method=umh
subq=9
me_range=16
g=50
keyint_min=25
sc_threshold=40
i_qfactor=0.71
b_strategy=2
qcomp=0.6
qmin=1
qmax=63
qdiff=4
refs=4
directpred=3
trellis=1
wpredp=2
dia_size=16
bf=8
level=41
nr=1000
aq_mode=1
aq_strength=1
```

The ffmpeg command line will be:

ffmpeg -fpre /tmp/ffmpeg.preset -strict experimental -vsync 1 -async  10000 INFILE -vcodec libx264 -crf 24 -acodec aac -ac 2 -ar 48000 -ab  128k -f mp4 OUTFILE_MP4

This encoding should result that the new file will be 1/10 of the original filesize.

---

### Post by hemertje on 2011-05-16
for info here:

[http://www.ffmpeg.org/ffmpeg-doc.html](http://www.ffmpeg.org/ffmpeg-doc.html)

**3.10 Preset files**

   A preset file contains a sequence of option=value pairs, one for each line, specifying a sequence of options which would be awkward to specify on the command line. Lines starting with the hash ('#') character are ignored and are used to provide comments. Check the `ffpresets' directory in the FFmpeg source tree for examples.   
 Preset files are specified with the vpre, apre, spre, and fpre options. The fpre option takes the filename of the preset instead of a preset name as input and can be used for any kind of codec. For the vpre, apre, and spre options, the options specified in a preset file are applied to the currently selected codec of the same type as the preset option.   
 The argument passed to the vpre, apre, and spre preset options identifies the preset file to use according to the following rules:   
 First ffmpeg searches for a file named arg.ffpreset in the directories `$FFMPEG_DATADIR' (if set), and `$HOME/.ffmpeg', and in the datadir defined at configuration time (usually `PREFIX/share/ffmpeg') in that order. For example, if the argument is libx264-max, it will search for the file `libx264-max.ffpreset'.   
 If no such file is found, then ffmpeg will search for a file named codec_name-arg.ffpreset in the above-mentioned directories, where codec_name is the name of the codec to which the preset file options will be applied. For example, if you select the video codec with -vcodec libx264 and use -vpre max, then it will search for the file `libx264-max.ffpreset'.

---

### Post by hemertje on 2011-05-16
strange

```
hemertje@hemertje-laptop:~/video$ ffmpeg -help
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:59:37, gcc: 4.4.3
ffmpeg: missing argument for option '-help'
hemertje@hemertje-laptop:~/video$ 

```

help isnt found ether...

---

### Post by hemertje on 2011-05-16
my fault, must be 
ffmpeg -h

---

### Post by hemertje on 2011-05-16
why is the official repo here in ubuntu still at version 0.5?

[http://www.ffmpeg.org/download.html](http://www.ffmpeg.org/download.html)

> ** FFmpeg 0.7-rc1 "Love and Peace"**

   0.7-rc1 was released on 2011-04-27. It is the latest FFmpeg release and is a copy of the oldabi branch at the time of release. It is therefor much more up to date than the previous 0.6.x releases. Amongst lots of other changes, ffmpeg-mt and libav trees have also been merged. 


---

### Post by andrew.46 on 2011-05-16
> **hemertje said:**
> why is the official repo here in ubuntu still at version 0.5?

Hence my question about your copy of FFmpeg :). For natty it is 0.6.2:

Package: ffmpeg (4:0.6.2-1ubuntu1) 
[http://packages.ubuntu.com/natty/ffmpeg](http://packages.ubuntu.com/natty/ffmpeg)

---

