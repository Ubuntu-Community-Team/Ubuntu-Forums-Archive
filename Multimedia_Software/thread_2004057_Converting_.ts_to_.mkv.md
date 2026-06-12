---
title: "Converting .ts to .mkv"
date: 2012-06-15
forum: Multimedia Software
---

### Post by johnaaronrose on 2012-06-15
I have recorded a .ts file to a memory stick using a pvr. I want to put them onto a DVD. So I thought that I should convert it, to say, a mkv format.


Using ffmpeg under Ubuntu 10.04: john@JohnDesktop:~/Temporary$ ffmpeg -i TheManchurianCandidate.ts  -vcodec copy -sameq -acodec copy -f matroska TheManchurianCandidate.mkv FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.3, Copyright (c) 2000-2009  Fabrice Bellard, et al.   configuration: --extra-version=4:0.5.1-1ubuntu1.3 --prefix=/usr  --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib  --enable-libgsm --enable-libschroedinger --enable-libspeex  --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib  --disable-stripping --disable-vhook --enable-runtime-cpudetect  --enable-gpl --enable-postproc --enable-swscale --enable-x11grab  --enable-libdc1394 --enable-shared --disable-static   libavutil     49.15. 0 / 49.15. 0   libavcodec    52.20. 1 / 52.20. 1   libavformat   52.31. 0 / 52.31. 0   libavdevice   52. 1. 0 / 52. 1. 0   libavfilter    0. 4. 0 /  0. 4. 0   libswscale     0. 7. 1 /  0. 7. 1   libpostproc   51. 2. 0 / 51. 2. 0   built on Dec 21 2011 18:41:38, gcc: 4.4.3 TheManchurianCandidate.ts: could not find codec parameters
  I have installed Restricted Extras & libdvdcss2. Is there another package that I have to install?


  Handbrake version 0.9.6 under Ubuntu 10.04 didn't work for me: I set  the Source to the .ts file and Handbrake scanned the Titles it didn't  find any and did not enable the Start button.

---

### Post by Jose Catre-Vandis on 2012-06-15
I use ProjectX (java app) to filter/re-index/whatever my ts files before encoding. This seems to sort out any A/V sync or indexing issues. Handy for getting rid of adverts too.

You don't need to use -sameq any more.

Why not just keep as a .ts file given you are not re-encoding in any way?

---

### Post by MartyBuntu on 2012-06-15
You need to demux the audio/video.

You AviDemux to bring the two files back together and then use HandBrake to create your .mkv file.

Here's a guide:

[https://help.ubuntu.com/community/Converting%20DVB-T%20streams%20to%20AVI%20files](https://help.ubuntu.com/community/Converting%20DVB-T%20streams%20to%20AVI%20files)

---

### Post by johnaaronrose on 2012-06-15
MartyBuntu,

Thanks for the help. I tried the procedure. A .m2v file was created but no .mp2/.ac3. A message "java.lang.ArrayIndexOutOfBoundsException: 71" appeared before "-> we have 312435 warnings/errors.".  Any ideas?

---

### Post by johnaaronrose on 2012-06-18
I forgot to mention that the exception occurred in ProjectX.

---

### Post by MartyBuntu on 2012-06-18
Is the .ts file playable?

---

### Post by johnaaronrose on 2012-06-18
No .ts file created by first using ProjectX.

If I don't use ProjectX but only use avidemux, .ts file is playable on PC but not recognised by Kogan TV when it is put on memory stick.

---

