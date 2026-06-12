---
title: "Copying cross-compiled ffmpeg to windows"
date: 2011-06-20
forum: Multimedia Software
---

### Post by marcjn on 2011-06-20
Hi,  I am new to this forum.  I installed Ubuntu in Virtualbox in a Windows XP platform, primarily to be able to cross compile ffmpeg and use it in Windows.
It's not been obvious, but I have a preliminary build in my Ubuntu system, that provides the following information, from the Ubuntu terminal:

 ```
FFmpeg version 0.6.2-4:0.6.21ubuntu1, Copyright (c)2000-2010 the Libav developers built on Mar 22 2011 15:55:04 with gcc 4.5.2
configuration: 
--extra-version=4:0.6.2-1ubuntu1 
--prefix=/usr
--enable-avfilter 
--enable-avfilter-lavf 
--enable-vdpau 
--enable-bzlib 
--enable-libgsm 
--enable-libschroedinger 
--enable-libspeex 
--enable-libtheora 
--enable-libvorbis 
--enable-pthreads 
--enable-zlib 
--enable-libvpx 
--disable-stripping 
--enable-runtime-cpudetect 
--enable-vaapi 
--enable-gpl 
--enable-postproc 
--enable-swscale 
--enable-x11grab 
--enable-libdc1394 
--enable-shared 
--disable-static
libavutil 50.15. 1 / 50.15. 1
libavcodec 52.72. 2 / 52.72. 2
libavformat 52.64. 2 / 52.64. 2
libavdevice 52. 2. 0 / 52. 2. 0
libavfilter 1.19. 0 / 1.19. 0
libswscale 0.11. 0 / 0.11. 0
libpostproc 51. 2. 0 / 51. 2. 0
Hyper fast Audio and Video encoder
```

When I copy the build folder to a USB drive (share folders with Windows are giving me headaches) and then to Windows, this ffmpeg application is telling me the following from the Windows command prompt:

```
FFmpeg version SVN-r26402, Copyright (c) 2000-2011 
the FFmpeg developers   built on Mar  3 2011 19:51:16 with gcc 4.4.2
  configuration: 
  --enable-memalign-hack 
  --arch=x86 
  --target-os=mingw32 
  --cross-prefix=i686-mingw32-
  libavutil     50.36. 0 / 50.36. 0
  libavcore      0.16. 1 /  0.16. 1
  libavcodec    52.108. 0 / 52.108. 0
  libavformat   52.93. 0 / 52.93. 0
  libavdevice   52. 2. 3 / 52. 2. 3
  libavfilter    1.74. 0 /  1.74. 0
  libswscale     0.12. 0 /  0.12. 0
Hyper fast Audio and Video encoder
```

Is it possible that when I compile ffmpeg under Ubuntu, the version I see in Windows looks that different?  Am I missing something obvious? Very perplexed !

Thanks for any help or any comment.
Jean

---

### Post by andrew.46 on 2011-06-21
Good on you for making such an effort! Were you tempted to try one of the static builds here:

Zeranoe FFmpeg builds
[http://ffmpeg.zeranoe.com/builds/](http://ffmpeg.zeranoe.com/builds/)

Your 2 builds represent 2 different versions by the look of it...

---

### Post by marcjn on 2011-06-21
Thanks Andrew.
I would use one of the Zeranoe builds, but I need a slightly different configuration.

---

