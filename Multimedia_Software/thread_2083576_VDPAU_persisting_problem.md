---
title: "VDPAU persisting problem"
date: 2012-11-13
forum: Multimedia Software
---

### Post by Decesive on 2012-11-13
Hello fellow Ubuntu Users,

I really hope you can help me out here, in your journey through Ubuntu you surely have stumbled upon VDPAU (if you have ever watched a 1080p movie), the problem is, I searched the entire universe of internet and cannot find a solution to my problem, VDPAU just doesn't like me or my GPU or my CPU, it won't start working, I'm using SMplayer with VDPAU setting for codec and default settings for configuration, my GPU is GTX 460 and I'm using Ubuntu 12.10, the error log looks like this:
(doesn't look like error actually but I know you can help me:)

 p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau, -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo vdpau -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 56623149 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/adminex/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -nocache -ss 72 -osdlevel 0 -noslices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/adminex/Downloads/[Final8]Mirai Nikki - 01-14 (BD 10-bit 1920x1080 x264 FLAC)/[Final8]Mirai Nikki - 08 (BD 10-bit 1920x1080 x264 FLAC)[217A3ABF].mkv
 

 MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 

 Playing /home/adminex/Downloads/[Final8]Mirai Nikki - 01-14 (BD 10-bit 1920x1080 x264 FLAC)/[Final8]Mirai Nikki - 08 (BD 10-bit 1920x1080 x264 FLAC)[217A3ABF].mkv.
 libavformat version 53.21.0 (external)
 Mismatching header version 53.19.0
 Configuration: --arch=i386 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.8.4-0ubuntu0.12.10.1' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-gnutls --enable-libgsm --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-swscale --enable-libcdio --enable-x11grab --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static
 libavformat file format detected.
 [matroska,webm @ 0xb6b63460]max_analyze_duration reached
 [matroska,webm @ 0xb6b63460]Estimating duration from bitrate, this may be inaccurate
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=30000
 ID_CHAPTER_0_NAME=Prologue
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=30000
 ID_CHAPTER_1_END=120000
 ID_CHAPTER_1_NAME=OP
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=120000
 ID_CHAPTER_2_END=710000
 ID_CHAPTER_2_NAME=Part A
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=710000
 ID_CHAPTER_3_END=1189500
 ID_CHAPTER_3_NAME=Part B
 ID_CHAPTER_ID=4
 ID_CHAPTER_4_START=1189500
 ID_CHAPTER_4_END=1279000
 ID_CHAPTER_4_NAME=ED
 ID_CHAPTER_ID=5
 ID_CHAPTER_5_START=1279000
 ID_CHAPTER_5_END=1428136
 ID_CHAPTER_5_NAME=Epilogue
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 [lavf] stream 1: audio (flac), -aid 0
 ID_SUBTITLE_ID=0
 [lavf] stream 2: subtitle (***), -sid 0
 VIDEO:  [H264]  1920x1080  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Load subtitles in /home/adminex/Downloads/[Final8]Mirai Nikki - 01-14 (BD 10-bit 1920x1080 x264 FLAC)/
 ID_FILENAME=/home/adminex/Downloads/[Final8]Mirai Nikki - 01-14 (BD 10-bit 1920x1080 x264 FLAC)/[Final8]Mirai Nikki - 08 (BD 10-bit 1920x1080 x264 FLAC)[217A3ABF].mkv
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=0
 ID_VIDEO_WIDTH=1920
 ID_VIDEO_HEIGHT=1080
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=1.7778
 ID_AUDIO_FORMAT=61868
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 ID_START_TIME=0.00
 ID_LENGTH=1428.14
 ID_SEEKABLE=1
 ID_CHAPTERS=6
 Opening video filter: [*** auto=1]
 Couldn't open video filter '***'.
 ***: cannot add video filter
 ==========================================================================
 Forced video codec: ffh264vdpau
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 libavcodec version 53.35.0 (external)
 Mismatching header version 53.32.2
 Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
 ==========================================================================
 ID_VIDEO_CODEC=ffh264vdpau
 ==========================================================================
 Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
 AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio)
 ==========================================================================
 AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
 ID_AUDIO_CODEC=ffflac
 Starting playback...
 

 

 MPlayer interrupted by signal 11 in module: decode video
 ID_SIGNAL=11
 - MPlayer crashed by bad usage of CPU/FPU/RAM.
   Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
   disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
 - MPlayer crashed. This shouldn't happen.
   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
   gcc version. If you think it's MPlayer's fault, please read
   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
   won't help unless you provide this information when reporting a possible bug.
  [ This binary of MPlayer in Debian is currently compiled with
    '--enable-debug'; the debugging symbols are in the package
    'mplayer-dbg'.]
 

Thanks in advance, since it's morning i'll be here in a couple of hours, see you then!

---

### Post by andrew.46 on 2012-11-13
Not sure where to start with that one, perhaps [cut the Gordian Knot]("http://en.wikipedia.org/wiki/Gordian_Knot") and build your own copy of MPlayer:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

Is there a crash when using a different -vo such as xv or x11?

---

### Post by Decesive on 2012-11-13
Thanks, you surely moved it a whole lot and gave me hope ; )

Unfortunately it still doesn't work, the problem just changed, if I run mplayer and start a video there's a load of bull saying:

[h264_vdpau @ 0x8d5f9e0]VDPAU decoding does not support video colorspace
[h264_vdpau @ 0x8d5f9e0]decode_slice_header error
[h264_vdpau @ 0x8d5f9e0]no frame!
Error while decoding frame!

Then it says that my PC is too slow and starts only audio, SMplayer works pretty much the same way (obviously) it just doesn't tell me what the problem is, it just starts and Video Output remains black.

I, again, searched for a solution for a while, found that ffmpeg patch, downloaded it from git installed but it just didn't change a thing, maybe I did something wrong, maybe the previous codecs I installed (by previous I mean before I even wrote here about the problem) are messing with the ones I have now, but I don't really know how could I possibly clean it up, since I'm a Ubuntu newbie.

---

### Post by andrew.46 on 2012-11-13
Can you give a download location for the anime file you are trying? Send the info by PM if it is a problem :).

---

### Post by Decesive on 2012-11-13
I really would send you a PM but you do not allow PMs ; )
So, here it is:

[http://final8.yolasite.com/](http://final8.yolasite.com/)   - Mirai Nikki

Please, be cautious, it may be inappropriate for kids, there's a bit of nudity ; )

Don't know how this is going to help you (or me), but enjoy ; )

---

### Post by BicyclerBoy on 2012-11-13
mediainfo report 720p24 high 10 H264 L5.1, 4:2:0 10bit
Some off the download links are  massively compressed (20-100x more than OTA broadcast).
I guess anime stuff compresses very well.

I fairly sure vdpau can not decode 10bit video & H264 > L4.1.
That is going to need new (not avail) h/w.

Often the reported encode levels (high 10 @L5.1) on DIY stuff is just made-up/wrong.
No BDs are 10bit either.

You can use -vo vdpau (presentation) but have to use CPU decoding.

---

### Post by andrew.46 on 2012-11-13
Indeed as Bicycler has stated MPlayer will not use vdpau for 10bit video. Looks like you have a few choices: either re-encode the video and use then vdpau or simply use an alternative -vo such as gl or xv (both worked nicely on my system). Nice anime btw :)

---

### Post by BicyclerBoy on 2012-11-14
you can still use vdpau rendering/presentation (-vo) with any decoder (-vc)..just not the other way around (well not yet on linux)

---

### Post by andrew.46 on 2012-11-14
> **BicyclerBoy said:**
> you can still use vdpau rendering/presentation (-vo) with any decoder (-vc)..just not the other way around (well not yet on linux)

I did not know that, thanks :)

---

### Post by Decesive on 2012-11-14
Well, ok, I guess I will have to download those 720p ones.

Thanks for your time and help.

Maybe one more thing, can I somehow view it on VirtualBox ? It doesn't seem too real, the VirutalBox uses a Virutal GPU obviously, but maybe you tried it and succeeded playing it.

P.S. Yeah, I haven't seen that good anime for a while now and in my (very precious, very thin) free time, I'd like to enjoy it ; )

---

### Post by BicyclerBoy on 2012-11-14
Decoding that 1080 download is no problem for CPU..the datarate is not very high. It is very low.
My HD video is typically 5GB/hr.

You need to setup mplayer to use a diff decoder.
Can not use -vc ffh264vdpau.

A core2duo can decode/play a BD without trouble..
It is any post-processing that is power hungry (de-interlacing/scaling/denoise/sharpening)  & you do not need to do any of that..

---

### Post by Decesive on 2012-11-15
Well, ok, if You say so, I'll try it, but after your last post I tried using a different decoder and didn't have any luck, in fact it lagged just as much as any other decoder, I used VDPAU for Video Ouput of course,  but still, I will test it. Thanks.

---

