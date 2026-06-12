---
title: "Stopmotion export error input file corrupt/truncated"
date: 2010-11-04
forum: Multimedia Software
---

### Post by jfed on 2010-11-04
've been making a stopmotion animation with my friend all day, and we imported it into the program StopMotion to turn it into an actual video. Every time i try to export it, it asks me where to save it, when i click save, i get an error message. 

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
libavutil 49.15. 0 / 49.15. 0
libavcodec 52.20. 0 / 52.20. 0
libavformat 52.31. 0 / 52.31. 0
libavdevice 52. 1. 0 / 52. 1. 0
libavfilter 0. 4. 0 / 0. 4. 0
libswscale 0. 7. 1 / 0. 7. 1
libpostproc 51. 2. 0 / 51. 2. 0
built on Apr 23 2010 15:05:49, gcc: 4.4.1
/home/justin/.stopmotion/packer/alienstopmotion1/images/%06d.jpg: I/O error occurred
Usually that means that input file is truncated and/or corrupted.

^Its telling me that an input file is truncated and or corrupted, i have no idea what truncated means. the line above it i think has something to do with one of the frames being messed up? honestly i'm clueless here, please help me. =(

---

### Post by bric on 2010-12-22
Did you find a solution? I just solved this exact problem.

My camera apparently has capital .JPG on the files (or the output from stopmotion was using .JPG) instead of ".jpg" (lower case).

The configuration line for ffmpeg in the stopmotion gui is set to use .jpg (lowercase) so you need to set that to be .JPG

Go to the settings > configure > video export tab > edit button

in the next dialogue box in the line that says "start encoder" you will see "%06.jpg" change that to "%06.JPG"

Then export and also, at this point I put an mp4 extension at the end of the filename I specified.

e.g., moviename.mp4

It worked! Though the quality is a bit lower than I would like.  I may have to read up on ffmpeg and play with the quality settings.

hope that helps

_**Question**_: If anyone knows how to put "either/or" in that configuration line let me know. (i.e., either .JPG or .jpg)

---

