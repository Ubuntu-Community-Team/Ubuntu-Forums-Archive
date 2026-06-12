---
title: "Trying to create a ffmpeg file that have xvid"
date: 2008-10-18
forum: Multimedia Software
---

### Post by cazz on 2008-10-18
Hi
I was going to try to use winff but I found out it say when I start to convert that the ffmpeg dont have xvid

It say 

Unknown codec xvid

After that I remove ffmpeg and install ffmpeg from medibuntu but after I have install winff it say same problem

after I have remove ffmpeg again I thinking about make my own ffmpeg from source but then I going to ./configure it say Unknown option "–enable-liba52".

I have try with both [https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg) and [http://www.zimbio.com/Ubuntu+Linux/articles/381/Ubuntu+YouTube+IPOD+Part+1+Downloading+converting](http://www.zimbio.com/Ubuntu+Linux/articles/381/Ubuntu+YouTube+IPOD+Part+1+Downloading+converting) but have same problem.

I have no idea what to do and why ffmpeg dont have xvid supported when xvid is free to use??

---

### Post by cor2y on 2008-10-18
Its been a while since i compiled ffmpeg (used to do it all the time until i realized the medibuntu version ships with all the libraries i need like amr support etc) but the syntax is wrong.
Before running ./configure run ./configure --help to see what libraries you need as well as the correct syntax, example its not -enable-liba52 but --enable-liba52 as for the xvid thing make sure if it is a custome compile that the development headers are installed as well as the library files.
Example libxvidcore as well as libxvidcore4-dev is installed via synaptic. Although i have heard ffmpeg now ships with native xvid support (this is the svn bleeding edge version not the one in the main ubuntu repo) your best bet if you don't want the hassle is to add the medibuntu repos and install its version of ffmpeg along with all the support files like libswscale etc (they all get installed by default when you select ffmpeg to be installed), they are relatively up to date and less hassle than a compile.

---

### Post by andrew.46 on 2008-11-20
Hi,

Have you checked the exact name of the xvid encoder:

```
andrew@skamandros:~$ ffmpeg -formats | grep xvid
FFmpeg version SVN-r15772, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-nonfree --enable-postproc 
--enable-pthreads --enable-libamr-nb --enable-libamr-wb --enable-libmp3lame 
--enable-libschroedinger --enable-libx264 --enable-libxvid
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 2. 0 / 52. 2. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Nov  4 2008 18:37:29, gcc: 4.3.2
  EV    libxvid         libxvidcore MPEG-4 part 2

```

I have 'libxvid' rather than 'xvid'. Can I suggest  look through the FakeOutdoorsman's ffmpeg thread on these forums where this issue has come up a few times:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

 Andrew

---

### Post by paul.gevers on 2008-12-04
> **cazz said:**
> Hi
I have no idea what to do and why ffmpeg dont have xvid supported when xvid is free to use??

If you are an intrepid user (Ubuntu 8.10) you want the libavcodec-unstripped-51 files. Easiest to install via ubuntu-restricted-extras (the last number increases once in a while.

So (depending on what you are using):
```
sudo install ubuntu-restricted-extras
```
or 
```
sudo install kubuntu-restricted-extras
```
or
```
sudo install xubuntu-restricted-extras
```

What version of winff do you have installed? You might need an other presets.xml file. See: [1] for newer presets files and [2] for installation.

[1] [http://code.google.com/p/winff/downloads/list](http://code.google.com/p/winff/downloads/list)
[2] [http://code.google.com/p/winff/wiki/InstallPresetsxml](http://code.google.com/p/winff/wiki/InstallPresetsxml)

---

### Post by sdowney717 on 2009-11-14
i cant configure it either!

> scott@scott-desktop:~/ffmpeg$ ./configure --enable-gpl --enable-liba52 --enable-libgsm --enable-libxvid --enable-libamr_nb --enable-libamr_wb --enable-libmp3lame --enable-libogg --enable-libvorbis --enable-libfaac --enable-libfaad --enable-shared --enable-nonfree
Unknown option "--enable-liba52".
See ./configure --help for available options.
scott@scott-desktop:~/ffmpeg$ 



[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)
[http://wesleybailey.com/articles/ffmpeg-tutorial-convert-avchd-mts-m2ts](http://wesleybailey.com/articles/ffmpeg-tutorial-convert-avchd-mts-m2ts)

It is the right syntax. something about liba52??

---

### Post by sdowney717 on 2009-11-14
can we get an undamaged version of libavcodec?

# --enable-liba52
This (optional because it modifies the licence of ffmpeg) library, liba52, which is part of libavcodec, contains the codec used to decode and encode AC3 audio commonly used on DVD-Videos.


> scott@scott-desktop:~/ffmpeg$ ./configure --help
Usage: configure [options]
Options: [defaults in brackets after descriptions]

Standard options:
  --help                   print this message
  --logfile=FILE           log tests and output to FILE [config.err]
  --disable-logging        do not log configure debug information
  --prefix=PREFIX          install in PREFIX []
  --bindir=DIR             install binaries in DIR [PREFIX/bin]
  --datadir=DIR            install data files in DIR [PREFIX/share/ffmpeg]
  --libdir=DIR             install libs in DIR [PREFIX/lib]
  --shlibdir=DIR           install shared libs in DIR [PREFIX/lib]
  --incdir=DIR             install includes in DIR [PREFIX/include]
  --mandir=DIR             install man page in DIR [PREFIX/share/man]

Configuration options:
  --disable-static         do not build static libraries [no]
  --enable-shared          build shared libraries [no]
  --enable-gpl             allow use of GPL code, the resulting libs
                           and binaries will be under GPL [no]
  --enable-version3        upgrade (L)GPL to version 3 [no]
  --enable-nonfree         allow use of nonfree code, the resulting libs
                           and binaries will be unredistributable [no]
  --disable-doc            do not build documentation
  --disable-ffmpeg         disable ffmpeg build
  --disable-ffplay         disable ffplay build
  --disable-ffserver       disable ffserver build
  --enable-postproc        enable GPLed postprocessing support [no]
  --enable-avfilter        video filter support [no]
  --enable-avfilter-lavf   video filters dependent on avformat [no]
  --enable-beosthreads     use BeOS threads [no]
  --enable-os2threads      use OS/2 threads [no]
  --enable-pthreads        use pthreads [no]
  --enable-w32threads      use Win32 threads [no]
  --enable-x11grab         enable X11 grabbing [no]
  --disable-network        disable network support [no]
  --disable-ipv6           disable IPv6 support [no]
  --disable-mpegaudio-hp   faster (but less accurate) MPEG audio decoding [no]
  --enable-gray            enable full grayscale support (slower color)
  --disable-swscale-alpha  disable alpha channel support in swscale
  --disable-fastdiv        disable table-based division
  --enable-small           optimize for size instead of speed
  --disable-aandct         disable AAN DCT code
  --disable-fft            disable FFT code
  --disable-golomb         disable Golomb code
  --disable-lpc            disable LPC code
  --disable-mdct           disable MDCT code
  --disable-rdft           disable RDFT code
  --disable-vaapi          disable VAAPI code
  --disable-vdpau          disable VDPAU code
  --enable-runtime-cpudetect detect cpu capabilities at runtime (bigger binary)
  --enable-hardcoded-tables use hardcoded tables instead of runtime generation
  --enable-memalign-hack   emulate memalign, interferes with memory debuggers
  --enable-beos-netserver  enable BeOS netserver
  --disable-encoder=NAME   disable encoder NAME
  --enable-encoder=NAME    enable encoder NAME
  --disable-encoders       disable all encoders
  --disable-decoder=NAME   disable decoder NAME
  --enable-decoder=NAME    enable decoder NAME
  --disable-decoders       disable all decoders
  --disable-hwaccel=NAME   disable hwaccel NAME
  --enable-hwaccel=NAME    enable hwaccel NAME
  --disable-hwaccels       disable all hwaccels
  --disable-muxer=NAME     disable muxer NAME
  --enable-muxer=NAME      enable muxer NAME
  --disable-muxers         disable all muxers
  --disable-demuxer=NAME   disable demuxer NAME
  --enable-demuxer=NAME    enable demuxer NAME
  --disable-demuxers       disable all demuxers
  --enable-parser=NAME     enable parser NAME
  --disable-parser=NAME    disable parser NAME
  --disable-parsers        disable all parsers
  --enable-bsf=NAME        enable bitstream filter NAME
  --disable-bsf=NAME       disable bitstream filter NAME
  --disable-bsfs           disable all bitstream filters
  --enable-protocol=NAME   enable protocol NAME
  --disable-protocol=NAME  disable protocol NAME
  --disable-protocols      disable all protocols
  --disable-indev=NAME     disable input device NAME
  --disable-outdev=NAME    disable output device NAME
  --disable-indevs         disable input devices
  --disable-outdevs        disable output devices
  --disable-devices        disable all devices
  --enable-filter=NAME     enable filter NAME
  --disable-filter=NAME    disable filter NAME
  --disable-filters        disable all filters
  --list-decoders          show all available decoders
  --list-encoders          show all available encoders
  --list-hwaccels          show all available hardware accelerators
  --list-muxers            show all available muxers
  --list-demuxers          show all available demuxers
  --list-parsers           show all available parsers
  --list-protocols         show all available protocols
  --list-bsfs              show all available bitstream filters
  --list-indevs            show all available input devices
  --list-outdevs           show all available output devices
  --list-filters           show all available filters

External library support:
  --enable-avisynth        enable reading of AVISynth script files [no]
  --enable-bzlib           enable bzlib [autodetect]
  --enable-libopencore-amrnb enable AMR-NB de/encoding via libopencore-amrnb [no]
  --enable-libopencore-amrwb enable AMR-WB decoding via libopencore-amrwb [no]
  --enable-libdc1394       enable IIDC-1394 grabbing using libdc1394
                           and libraw1394 [no]
  --enable-libdirac        enable Dirac support via libdirac [no]
  --enable-libfaac         enable FAAC support via libfaac [no]
  --enable-libfaad         enable FAAD support via libfaad [no]
  --enable-libfaadbin      open libfaad.so.0 at runtime [no]
  --enable-libgsm          enable GSM support via libgsm [no]
  --enable-libmp3lame      enable MP3 encoding via libmp3lame [no]
  --enable-libnut          enable NUT (de)muxing via libnut,
                           native (de)muxer exists [no]
  --enable-libopenjpeg     enable JPEG 2000 decoding via OpenJPEG [no]
  --enable-libschroedinger enable Dirac support via libschroedinger [no]
  --enable-libspeex        enable Speex decoding via libspeex [no]
  --enable-libtheora       enable Theora encoding via libtheora [no]
  --enable-libvorbis       enable Vorbis encoding via libvorbis,
                           native implementation exists [no]
  --enable-libx264         enable H.264 encoding via x264 [no]
  --enable-libxvid         enable Xvid encoding via xvidcore,
                           native MPEG-4/Xvid encoder exists [no]
  --enable-mlib            enable Sun medialib [no]
  --enable-zlib            enable zlib [autodetect]

Advanced options (experts only):
  --source-path=PATH       path to source code [/home/scott/ffmpeg]
  --cross-prefix=PREFIX    use PREFIX for compilation tools []
  --enable-cross-compile   assume a cross-compiler is used
  --sysroot=PATH           root of cross-build tree
  --sysinclude=PATH        location of cross-build system headers
  --target-os=OS           compiler targets OS [linux]
  --target-exec=CMD        command to run executables on target
  --target-path=DIR        path to view of build directory on target
  --nm=NM                  use nm tool
  --as=AS                  use assembler AS []
  --cc=CC                  use C compiler CC [gcc]
  --ld=LD                  use linker LD
  --host-cc=HOSTCC         use host C compiler HOSTCC
  --host-cflags=HCFLAGS    use HCFLAGS when compiling for host
  --host-ldflags=HLDFLAGS  use HLDFLAGS when linking for host
  --host-libs=HLIBS        use libs HLIBS when linking for host
  --extra-cflags=ECFLAGS   add ECFLAGS to CFLAGS []
  --extra-ldflags=ELDFLAGS add ELDFLAGS to LDFLAGS []
  --extra-libs=ELIBS       add ELIBS []
  --extra-version=STRING   version string suffix []
  --build-suffix=SUFFIX    library name suffix []
  --arch=ARCH              select architecture [i686]
  --cpu=CPU                select the minimum required CPU (affects
                           instruction selection, may crash on older CPUs)
  --enable-powerpc-perf    enable performance report on PPC
                           (requires enabling PMC)
  --disable-altivec        disable AltiVec optimizations
  --disable-amd3dnow       disable 3DNow! optimizations
  --disable-amd3dnowext    disable 3DNow! extended optimizations
  --disable-mmx            disable MMX optimizations
  --disable-mmx2           disable MMX2 optimizations
  --disable-sse            disable SSE optimizations
  --disable-ssse3          disable SSSE3 optimizations
  --disable-armv5te        disable armv5te optimizations
  --disable-armv6          disable armv6 optimizations
  --disable-armv6t2        disable armv6t2 optimizations
  --disable-armvfp         disable ARM VFP optimizations
  --disable-iwmmxt         disable iwmmxt optimizations
  --disable-mmi            disable MMI optimizations
  --disable-neon           disable neon optimizations
  --disable-vis            disable VIS optimizations
  --disable-yasm           disable use of yasm assembler
  --enable-pic             build position-independent code

Developer options (useful when working on FFmpeg itself):
  --disable-debug          disable debugging symbols
  --enable-debug=LEVEL     set the debug level []
  --enable-gprof           enable profiling with gprof []
  --disable-optimizations  disable compiler optimizations
  --enable-extra-warnings  enable more compiler warnings
  --disable-stripping      disable stripping of executables and shared libraries

NOTE: Object files are built at the place where configure is launched.
scott@scott-desktop:~/ffmpeg$ 


---

### Post by paul.gevers on 2009-11-14
> **sdowney717 said:**
> can we get an undamaged version of libavcodec?

# --enable-liba52
This (optional because it modifies the licence of ffmpeg) library, liba52, which is part of libavcodec, contains the codec used to decode and encode AC3 audio commonly used on DVD-Videos.

I haven't inspected myself, but seeing this behavior it looks like this option has been removed. And if you have the libavcodec-extra-52 or libavcodec-unstripped-51 (depending if you are using Jaunty or Karmic) you already have the best there is possible in Ubuntu. You might however try a [PPA]("https://launchpad.net/ubuntu/+ppas?name_filter=ffmpeg")

---

### Post by sdowney717 on 2009-11-14
yes i think so too.

I managed to configure and compile with this line

> ./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora          --enable-libxvid --enable-libvorbis --enable-avfilter --enable-bzlib --enable-libdirac --enable-postproc --enable-x11grab --enable-shared 


and i have mencoder compiled too.

WHAT i would like to do is create video files with mpeg 1 layer3 audio
I have a media player that likes that and dislikes mpeg 2 layer3 audio

there is a diff and i am stuck. the player is ok with mpeg1,2,4, divx, xvid video
for audio PCM audio and  mpeg1 layer mp3  MPEG 1 Audio, Layer 2 audio

---

### Post by sdowney717 on 2009-11-14
mencoder evening_broadcast1109_720.mp4 -o 122aoutputmpeg.divx -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=30 -ffourcc DIVX -oac twolame -twolameopts br=224

Ok, i got it, this makes a mpeg1 layer2 audio, but this one plays with a hiss
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html)

now i need mpeg1 layer3

---

### Post by paul.gevers on 2009-11-14
> **sdowney717 said:**
> there is a diff and i am stuck. the player is ok with mpeg1,2,4, divx, xvid video
for audio PCM audio and  mpeg1 layer mp3  MPEG 1 Audio, Layer 2 audio

I am not familiar with the info in the screenshots, but maybe it helps to get the info from ffmpeg. What does ```
ffmpeg -i <filename>
``` give for a video that works? Try to get the same settings.

When I do ```
ffmpeg -formats | grep mpeg
``` I get a LOT of response. It seems like it is a matter of finding the right setting.

---

### Post by sdowney717 on 2009-11-14
ok here are 2 files, one is fine other is not
the first one is listed as mpeg 1 layer 3 sound
the second one in the ubuntu property window is listed as mpeg2 layer 3 sound

ffmpeg seems to show the only diff is 44100hz 24000hz

> 
This one plays fine

scott@scott-desktop:~/Videos$ ffmpeg -i 122dcboutputmpeg.divx
FFmpeg version SVN-r20533, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 14 2009 09:37:46 with gcc 4.4.1
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libxvid --enable-libvorbis --enable-avfilter --enable-bzlib --enable-libdirac --enable-postproc --enable-x11grab
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1. 8. 0 /  1. 8. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, avi, from '122dcboutputmpeg.divx':
  Duration: 00:21:27.68, start: 0.000000, bitrate: 1239 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 30k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 128 kb/s
At least one output file must be specified

This one plays with a hiss, video is fine, sound hisses white noise

scott@scott-desktop:~/Videos$ ffmpeg -i 122acboutputmpeg.divx
FFmpeg version SVN-r20533, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 14 2009 09:37:46 with gcc 4.4.1
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libxvid --enable-libvorbis --enable-avfilter --enable-bzlib --enable-libdirac --enable-postproc --enable-x11grab
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1. 8. 0 /  1. 8. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 16999.00 (16999/1) -> 23.98 (24000/1001)
Input #0, avi, from '122acboutputmpeg.divx':
  Duration: 00:01:47.16, start: 0.000000, bitrate: 1145 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x272 [PAR 1:1 DAR 40:17], 23.98 tbr, 23.98 tbn, 16999 tbc
    Stream #0.1: Audio: mp3, 24000 Hz, 2 channels, s16, 128 kb/s
At least one output file must be specified
scott@scott-desktop:~/Videos$

---

### Post by sdowney717 on 2009-11-14
using mencoder this makes it mpeg1 layer3 mp3!, if it is originally MPEG-4 AAC audio 
if original file is mpeg2 layer 3 it leaves it unchanged
it is like an audio copy. How can you force mencoder to transcode the audio?

> 
mencoder evening_broadcast1109_720.mp4 -o 122dcboutputmpeg.divx  -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame -lameopts cbr:br=128



according to their own site it is supposed to do mpeg1 layer 3!

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html#menc-feat-enc-libavcodec-audio-codecs](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html#menc-feat-enc-libavcodec-audio-codecs)

> 
Audio codec name	Description
ac3	Dolby Digital (AC-3)
adpcm_*	Adaptive PCM formats - see supplementary table
flac	Free Lossless Audio Codec (FLAC)
g726	G.726 ADPCM
libfaac	Advanced Audio Coding (AAC) - using FAAC
libgsm	ETSI GSM 06.10 full rate
libgsm_ms	Microsoft GSM


libmp3lame	MPEG-1 audio layer 3 (MP3) - using LAME


mp2	MPEG-1 audio layer 2 (MP2)
pcm_*	PCM formats - see supplementary table
roq_dpcm	Id Software RoQ DPCM
sonic	experimental FFmpeg lossy codec
sonicls	experimental FFmpeg lossless codec
vorbis	Vorbis
wmav1	Windows Media Audio v1
wmav2	Windows Media Audio v2

---

