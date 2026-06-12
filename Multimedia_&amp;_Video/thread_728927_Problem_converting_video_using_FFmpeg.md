---
title: "Problem converting video using FFmpeg"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by James- on 2008-03-19
I'm trying to convert a video for my ps3 using ffmpeg with the fallowing code:

```
ffmpeg -i ~/Shared/video.avi -y -vcodec libx264 -acodec libfaac -title 'Home Video' -f mp4 -mbd rd -flags 4mv+trell+aic+qprd+mv0 -cmp 2 -subcmp 2 -flags2 dct8x8+skiprd -level 41 -b 20000 -bf 3 -ac 2 -ab 24000 -threads 1 -pass 2 ~/Shared/videooutput.mp4
```

and I get the fallowing bash error:

```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, avi, from '/home/james/Shared/video.avi':
  Duration: 02:05:55.9, start: 0.000000, bitrate: 778 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 564x300, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 96 kb/s
Unknown codec 'libx264'

```

---

### Post by xzero1 on 2008-03-19
It can't find the x264 codec. You might need to get an updated version or compile the source to get it.

---

### Post by eye208 on 2008-03-19
... or use MEncoder instead.

---

### Post by philc on 2008-03-19
Your error indicates that the version of FFmpeg you are using doesn't have x264 enabled. This could be either that libx264 is not installed, or it wasn't enabled at compile time.

To fix this you'll need to install libx264 and re-compile FFmpeg, with that library enabled.

Here's a link that might help:

[http://stream0.org/2008/01/install-ffmpeg-on-debian-etch.html](http://stream0.org/2008/01/install-ffmpeg-on-debian-etch.html)

---

### Post by James- on 2008-03-20
> **philc said:**
> Your error indicates that the version of FFmpeg you are using doesn't have x264 enabled. This could be either that libx264 is not installed, or it wasn't enabled at compile time.

To fix this you'll need to install libx264 and re-compile FFmpeg, with that library enabled.

Here's a link that might help:

[http://stream0.org/2008/01/install-ffmpeg-on-debian-etch.html](http://stream0.org/2008/01/install-ffmpeg-on-debian-etch.html)

and is mpeg4 enabled by default? Sorry I'm new to recompiling programs

while I was running the compile it says:
> 
james@james-laptop-linux:~/ffmpeg-compile/ffmpeg$ ./configure --enable-gpl --enable-postproc --enable-libvorbis --enable-liba52 --enable-libdc1394 --enable-libgsm --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-pthreads --enable-libx264 -enable-libxvid --enable-shared
Unknown option "-enable-libxvid".
See ./configure --help for available options.


and in ./configure --help it has the --enablelibxvid

I have the libxvidcore4 and libxcore4-dev packages......

---

### Post by mc4man on 2008-03-20
> -enable-libxvid
```
--enable-libxvid
```  
here's another alt. app
[http://h264enc.sourceforge.net/](http://h264enc.sourceforge.net/)

---

### Post by zenrox on 2008-03-20
```

 ./configure --help
Usage: configure [options]
Options: [defaults in brackets after descriptions]

Standard options:
  --help                   print this message
  --log[=FILE|yes|no]      log tests and output to FILE [config.err]
  --prefix=PREFIX          install in PREFIX [/usr/local]
  --libdir=DIR             install libs in DIR [PREFIX/lib]
  --shlibdir=DIR           install shared libs in DIR [PREFIX/lib]
  --incdir=DIR             install includes in DIR [PREFIX/include/ffmpeg]
  --mandir=DIR             install man page in DIR [PREFIX/man]
  --enable-mingwce         enable MinGW native/cross WinCE compile
  --enable-static          build static libraries [default=yes]
  --disable-static         do not build static libraries [default=no]
  --enable-shared          build shared libraries [default=no]
  --disable-shared         do not build shared libraries [default=yes]
  --enable-gpl             allow use of GPL code, the resulting libav*
                           and ffmpeg will be under GPL [default=no]
  --enable-pp              enable GPLed postprocessing support [default=no]
  --enable-swscaler        software scaler support [default=no]
  --enable-beosthreads     use BeOS threads [default=no]
  --enable-os2threads      use OS/2 threads [default=no]
  --enable-pthreads        use pthreads [default=no]
  --enable-w32threads      use Win32 threads [default=no]
  --enable-x11grab         enable X11 grabbing [default=no]

External library support:
  --enable-sunmlib         use Sun medialib [default=no]
  --enable-dc1394          enable IIDC-1394 grabbing using libdc1394
                           and libraw1394 [default=no]
  --enable-liba52          enable GPLed liba52 support [default=no]
  --enable-liba52bin       open liba52.so.0 at runtime [default=no]
  --enable-avisynth        allow reading AVISynth script files [default=no]
  --enable-libdts          enable GPLed libdts support [default=no]
  --enable-libfaac         enable FAAC support via libfaac [default=no]
  --enable-libfaad         enable FAAD support via libfaad [default=no]
  --enable-libfaadbin      build FAAD support with runtime linking [default=no]
  --enable-libgsm          enable GSM support via libgsm [default=no]
  --enable-libmp3lame      enable MP3 encoding via libmp3lame [default=no]
  --enable-libnut          enable NUT (de)muxing via libnut,
                           native demuxer exists [default=no]
  --enable-libogg          enable Ogg muxing via libogg [default=no]
  --enable-libtheora       enable Theora encoding via libtheora [default=no]
  --enable-libvorbis       enable Vorbis en/decoding via libvorbis,
                           native implementations exist [default=no]
  --enable-x264            enable H.264 encoding via x264 [default=no]
  --enable-xvid            enable Xvid encoding via xvidcore,
                           native MPEG-4/Xvid encoder exists [default=no]
  --enable-amr_nb          enable amr_nb float audio codec
  --enable-amr_nb-fixed    use fixed point for amr-nb codec
  --enable-amr_wb          enable amr_wb float audio codec
  --enable-amr_if2         enable amr_wb IF2 audio codec

Advanced options (experts only):
  --source-path=PATH       path to source code [/home/kergan/compiling/ffmpeg-0.cvs20070307]
  --cross-prefix=PREFIX    use PREFIX for compilation tools []
  --cross-compile          assume a cross-compiler is used
  --target-os=OS           compiler targets OS [Linux]
  --cc=CC                  use C compiler CC [gcc]
  --make=MAKE              use specified make [make]
  --extra-cflags=ECFLAGS   add ECFLAGS to CFLAGS []
  --extra-ldflags=ELDFLAGS add ELDFLAGS to LDFLAGS []
  --extra-libs=ELIBS       add ELIBS []
  --build-suffix=SUFFIX    suffix for application specific build []
  --arch=ARCH              select architecture  [i686]
  --cpu=CPU                selects the minimum cpu required (affects
                           instruction selection, may crash on older CPUs)
  --enable-powerpc-perf    enable performance report on PPC
                           (requires enabling PMC)
  --disable-mmx            disable MMX usage
  --disable-armv5te        disable armv5te usage
  --disable-armv6          disable armv6 usage
  --disable-iwmmxt         disable iwmmxt usage
  --disable-altivec        disable AltiVec usage
  --disable-audio-oss      disable OSS audio support [default=no]
  --disable-audio-beos     disable BeOS audio support [default=no]
  --disable-v4l            disable video4linux grabbing [default=no]
  --disable-v4l2           disable video4linux2 grabbing [default=no]
  --disable-bktr           disable bktr video grabbing [default=no]
  --disable-dv1394         disable DV1394 grabbing [default=no]
  --disable-network        disable network support [default=no]
  --disable-ipv6           disable ipv6 support [default=no]
  --disable-zlib           disable zlib [default=no]
  --disable-vhook          disable video hooking support
  --disable-debug          disable debugging symbols
  --disable-mpegaudio-hp   faster (but less accurate)
                           MPEG audio decoding [default=no]
  --disable-protocols      disable I/O protocols support [default=no]
  --disable-ffmpeg         disable ffmpeg build
  --disable-ffserver       disable ffserver build
  --disable-ffplay         disable ffplay build
  --enable-small           optimize for size instead of speed
  --enable-memalign-hack   emulate memalign, interferes with memory debuggers
  --disable-encoder=NAME   disables encoder NAME
  --enable-encoder=NAME    enables encoder NAME
  --disable-decoder=NAME   disables decoder NAME
  --enable-decoder=NAME    enables decoder NAME
  --disable-encoders       disables all encoders
  --disable-decoders       disables all decoders
  --disable-muxer=NAME     disables muxer NAME
  --enable-muxer=NAME      enables muxer NAME
  --disable-muxers         disables all muxers
  --disable-demuxer=NAME   disables demuxer NAME
  --enable-demuxer=NAME    enables demuxer NAME
  --disable-demuxers       disables all demuxers
  --enable-parser=NAME     enables parser NAME
  --disable-parser=NAME    disables parser NAME
  --disable-parsers        disables all parsers

Developer options (useful when working on FFmpeg itself):
  --enable-gprof           enable profiling with gprof [no]
  --disable-opts           disable compiler optimizations
  --enable-extra-warnings  enable more compiler warnings
  --disable-strip          disable stripping of executables and shared libraries


```
how about the help from the package made for ubuntu

---

