---
title: "ffmpeg version 2.5.8  on ubuntu 14.04"
date: 2015-09-23
forum: Multimedia Software
---

### Post by rmstock2 on 2015-09-23
If someone buys a BMW and wants it tuned, he/she has to drive below 4000 rpms to his
favorate tune shop to install some mandatory hardware. I was surprised to see that a package like ffmpeg, 
which is the one-stop tuning-kit for AV on Linux was pulled from ubuntu 14.04 :

Is FFmpeg missing from the official repositories in 14.04?
[http://askubuntu.com/questions/432542/is-ffmpeg-missing-from-the-official-repositories-in-14-04](http://askubuntu.com/questions/432542/is-ffmpeg-missing-from-the-official-repositories-in-14-04)
and read there that :
> 
The transitional ffmpeg package seems to have been removed from
trusty/Ubuntu 14.04 (compare the package files listing for saucy and     
trusty of the source package).

So here's my version of ffmpeg which is a rebuild of Version: 7:2.5.8-0ubuntu0.15.04.1
on  ubuntu14.04 :

[ftp://ftp.crashrecovery.org/pub/linux/ffmpeg/DEB/ubuntu1404/](ftp://ftp.crashrecovery.org/pub/linux/ffmpeg/DEB/ubuntu1404/)

As ffmpeg uses quite some .asm code and the libx265 HIGH_BIT_DEPTH=1
build for 32-bit x86 is not officially supported, ffmpeg is split here
in two seperate directories amd64 and i386.

[ftp://ftp.crashrecovery.org/pub/linux/ffmpeg/DEB/ubuntu1404/i386](ftp://ftp.crashrecovery.org/pub/linux/ffmpeg/DEB/ubuntu1404/i386)
[ftp://ftp.crashrecovery.org/pub/linux/ffmpeg/DEB/ubuntu1404/amd64](ftp://ftp.crashrecovery.org/pub/linux/ffmpeg/DEB/ubuntu1404/amd64)

The installation log : [ftp://ftp.crashrecovery.org/pub/linux/ffmpeg/DEB/ubuntu1404/amd64/install-log-ffmpeg-ubu14.04.3-TLS.html](ftp://ftp.crashrecovery.org/pub/linux/ffmpeg/DEB/ubuntu1404/amd64/install-log-ffmpeg-ubu14.04.3-TLS.html)
```

[SIZE=2]stock@acer30u:~$ ffmpeg 
ffmpeg version 2.5.8-0ubuntu0.15.04.1 Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04)
  configuration: --prefix=/usr --extra-version=0ubuntu0.15.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --shlibdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --enable-shared --disable-stripping --enable-avresample --enable-avisynth --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libshine --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libwavpack --enable-libwebp --enable-libxvid --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzvbi --enable-libzmq --enable-frei0r --enable-libvpx --enable-libx264 --enable-libsoxr --enable-gnutls --enable-openal --enable-libopencv --enable-librtmp --enable-libx265
  libavutil      54. 15.100 / 54. 15.100
  libavcodec     56. 13.100 / 56. 13.100
  libavformat    56. 15.102 / 56. 15.102
  libavdevice    56.  3.100 / 56.  3.100
  libavfilter     5.  2.103 /  5.  2.103
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  1.100 /  1.  1.100
  libpostproc    53.  3.100 / 53.  3.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'
stock@acer30u:~$ 
[/SIZE]
```

ffmpeg uses the new libx265 on both i386 and amd64, but a warning is in place :

> 
Issues
Create issue
Issue #150 closed
Linux x86 32 bit Yasm error
[https://bitbucket.org/multicoreware/x265/issues/150/linux-x86-32-bit-yasm-error](https://bitbucket.org/multicoreware/x265/issues/150/linux-x86-32-bit-yasm-error)

djcj created an issue 2015-06-28

Compiling with ASM on Linux x86 32 bit fails. Compiling on x86 64 bit 
works without any problems.

[ 37%] Building ASM_YASM object common/CMakeFiles/common.dir/x86/sad16-a.asm.o
    cd /tmp/buildd/x265-1.7+247/x265-10bit/common && /usr/bin/yasm -f elf32 
      -DARCH_X86_64=0 -DHAVE_ALIGNED_STACK=1 -DHIGH_BIT_DEPTH=1 
      -DBIT_DEPTH=10 -DX265_NS=x265  -o CMakeFiles/common.dir/x86/sad16-a.asm.o 
    /tmp/buildd/x265-1.7+247/source/common/x86/sad16-a.asm
    /tmp/buildd/x265-1.7+247/source/common/x86/sad16-a.asm:380: error: 
        undefined symbol `m8' (first use)
    /tmp/buildd/x265-1.7+247/source/common/x86/sad16-a.asm:380: error:  
        (Each undefined symbol is reported only once.)
    /tmp/buildd/x265-1.7+247/source/common/x86/sad16-a.asm:380: error: 
        (HADDUWD:1) undefined symbol `sizeofm8' in preprocessor
    /tmp/buildd/x265-1.7+247/source/common/x86/sad16-a.asm:380: error: 
        (HADDD:1) undefined symbol `sizeofm8' in preprocessor
    /tmp/buildd/x265-1.7+247/source/common/x86/sad16-a.asm:380: error: 
        (HADDD:8) undefined symbol `sizeofm8' in preprocessor
        common/CMakeFiles/common.dir/build.make:207: recipe for target 
        'common/CMakeFiles/common.dir/x86/sad16-a.asm.o' failed
    make[4]: *** [common/CMakeFiles/common.dir/x86/sad16-a.asm.o] Error 1

  nandaku2
  HIGH_BIT_DEPTH=1 build for 32-bit x86 is not officially supported.
      * 2015-06-29T13:26:14+00:00

  nandaku2
      * changed status to closed
      * 2015-06-29T13:26:37+00:00


---

