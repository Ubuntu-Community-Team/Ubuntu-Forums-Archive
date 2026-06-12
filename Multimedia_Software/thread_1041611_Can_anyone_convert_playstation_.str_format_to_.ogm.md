---
title: "Can anyone convert playstation .str format to .ogm?"
date: 2009-01-16
forum: Multimedia Software
---

### Post by IanVonSpeedfreak on 2009-01-16
For anyone that doesn't know .str is one of the common formats used for Playstation cinematics.  Anyone who has actually placed a PS1 (and I believe some PS2) game in their CD/DVD-ROM has probably come across these files in .str format (usually under some folder titled "movies").  Anyway, I've converted .str files before using a program on Windows called "MediaCoder".  Last I checked, the program didn't have much support and was dying - it may actually be the program now referred to as "SUPER".  Pardon, I guess I'm not getting to the point.

What I understand about these programs is that they're both simply front-ends for FFmpeg.  So I know that FFmpeg is capable of playing/converting .str files, I just don't know how to operate it from the command or know of a front-end that will allow me to convert .str files.  I have the Medibuntu version of FFmpeg, and I ran the command "ffmpeg -formats" and found the Playstation .str format listed explicitly so there should be some way of utilizing it.  My question is, has anyone tried it?  Does anyone know of a way to convert .str to any other format (preferably a high quality .ogm).

---

### Post by IanVonSpeedfreak on 2009-01-17
bump

---

### Post by FakeOutdoorsman on 2009-01-17
You could try something like this (using Medibuntu ffmpeg on Hardy):
```
ffmpeg -i input.str -ac 2 -vcodec libtheora output.ogg
```
or if that fails:
```
ffmpeg -f psxstr -i input.str -ac 2 -vcodec libtheora output.ogg
```
However, I kept getting segmentation faults in both Hardy Medibuntu ffmpeg and Arch Linux svn ffmpeg while trying to decode .str.  I'm assuming you are on Hardy since there is no Medibuntu ffmpeg for Intrepid.

---

### Post by IanVonSpeedfreak on 2009-01-17
Indeed, I am using Hardy Heron, sorry I didn't point that out (pardon, I hadn't updated my profile info).

So yeah, this the output from the first command:
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
/media/cdrom0/movie/capcom15.str: Unknown format
```

and this is the output of the second:

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
/media/cdrom0/movie/capcom15.str: I/O error occured
Usually that means that input file is truncated and/or corrupted.
```

Could it be that the error from the second command happens because I'm encoding straight from the disc?  Also, have you had any luck encoding to different formats?  What command is used to encode to .avi - that's what I commonly used to encode using MediaCoder on Windows?

btw, thanks for the help.

---

### Post by FakeOutdoorsman on 2009-01-19
> **IanVonSpeedfreak said:**
> Could it be that the error from the second command happens because I'm encoding straight from the disc?
It could be.  I've never tried encoding from a disc before.
> Also, have you had any luck encoding to different formats?
No, because it always fails during decoding of the .str, so I can't even get to the encoding step.  This might be bug report worthy for ffmpeg.
> What command is used to encode to .avi - that's what I commonly used to encode using MediaCoder on Windows?
The simplest is:
```
ffmpeg -i input.str output.avi
```
However, avi is just a container format and is used by various codecs: mpeg4, dvvideo, motion jpeg, etc.  By default, ffmpeg will choose mpeg4 unless you tell it otherwise.

---

