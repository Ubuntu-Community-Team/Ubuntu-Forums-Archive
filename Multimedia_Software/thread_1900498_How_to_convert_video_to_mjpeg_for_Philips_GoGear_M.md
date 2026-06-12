---
title: "How to convert video to mjpeg for Philips GoGear MP4 Player?"
date: 2011-12-26
forum: Multimedia Software
---

### Post by CarlWalters on 2011-12-26
I'm running Ubuntu 11.10 and I'm trying to convert video to a format acceptable by my daughters mp4 player which is a Philips GoGear SA3VBE04.  The Philips information says that it plays "Supported formats:MJPEG (in .mp4)". I've tried using ffmpeg on the command line like this 

```

ffmpeg -i  tmp.mp4 -s 128x128 -vcodec mjpeg -acodec adpcm_ima_wav -ar 22050 output.mp4

```

But I get error messages 
```

ffmpeg -i  tmp.mp4 -s 128x128 -vcodec mjpeg -acodec adpcm_ima_wav -ar 22050 output.mp4
ffmpeg version 0.7.2-4:0.7.2-1ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Oct  2 2011 15:12:32 with gcc 4.6.1
  configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.2.1ubuntu1+medibuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.2.1ubuntu1+medibuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  5. 0 / 53.  5. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'tmp.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isomavc1mp42
    creation_time   : 2010-12-09 10:41:13
  Duration: 00:00:30.00, start: 0.000000, bitrate: 576 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16, 99 kb/s
    Metadata:
      creation_time   : 2010-12-09 10:41:13
    Stream #0.1(und): Video: h264 (Constrained Baseline), yuv420p, 480x270 [PAR 1:1 DAR 16:9], 473 kb/s, 25 fps, 25 tbr, 25k tbn, 50 tbc
    Metadata:
      creation_time   : 2010-12-09 10:41:13
Incompatible pixel format 'yuv420p' for codec 'mjpeg', auto-selecting format 'yuvj420p'
[buffer @ 0x8f263a0] w:480 h:270 pixfmt:yuv420p
[scale @ 0x8f23fc0] w:480 h:270 fmt:yuv420p -> w:128 h:128 fmt:yuvj420p flags:0x4
[mp4 @ 0x8f22ac0] track 1: could not find tag, codec not currently supported in container
Output #0, mp4, to 'output.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isomavc1mp42
    creation_time   : 2010-12-09 10:41:13
    encoder         : Lavf53.2.0
    Stream #0.0(und): Video: mjpeg, yuvj420p, 128x128 [PAR 1:1 DAR 1:1], q=2-31, 200 kb/s, 25 tbn, 25 tbc
    Metadata:
      creation_time   : 2010-12-09 10:41:13
    Stream #0.1(und): Audio: adpcm_ima_wav, 22050 Hz, stereo, s16, 176 kb/s
    Metadata:
      creation_time   : 2010-12-09 10:41:13
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Could not write header for output file #0 (incorrect codec parameters ?)


```

And I've no idea what I'm doing wrong or even if there is an easier way to do this? 

Any help or advice would be very welcome.  Many thanks in advance.

---

### Post by wolfen69 on 2011-12-26
You could just use winff or handbrake to convert to .mp4. Both are gui apps and have worked well for me.

Winff is in the repos, and for Handbrake do:
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots && sudo apt-get update
```
then
```
sudo apt-get install handbrake-gtk
```

---

### Post by CarlWalters on 2011-12-27
> **wolfen69 said:**
> You could just use winff or handbrake to convert to .mp4. Both are gui apps and have worked well for me.

Thanks for the reply Wolfen69.

> **wolfen69 said:**
> Winff is in the repos, and for Handbrake do:
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots && sudo apt-get update
```
then
```
sudo apt-get install handbrake-gtk
```

I've now installed WinFF and Handbrake.  I didn't know that you could concatenate on the command line with && - very useful :) 

However there doesn't seem to be an option in either of them to convert to MJPEG.  There was small sample video on the device itself which works. 
So I've copied that across to my machine and loaded it up into HandBrake just to see what video parameters it reports and it shows the following

Source Picture Parameters
Source Codec          : mjpeg
Dimensions            : 160 x 128
Aspect                : 5:4
Frame Rate            : 24

Cropping
AutoCrop              : On
Crop                  : 0:0:0:0
Crop Dimensions       : 160 x 128

Scaling 
Scale Dimensions      : 160 x 128
Optional for Source   : Off
Anamorphic            : Loose

---

### Post by ron999 on 2011-12-27
Hi
More information about the sample video is needed.
Use MediaInfo, or upload it somewhere.

---

### Post by CarlWalters on 2011-12-28
> **ron999 said:**
> Hi
More information about the sample video is needed.
Use MediaInfo, or upload it somewhere.

OK - I've installed mediainfo v0.7.50 and run it on the sample video file to give this output

```

General
Complete name                            : ../../Formula 1.mp4
Format                                   : MPEG-4
Format profile                           : QuickTime
Codec ID                                 : qt  
File size                                : 9.18 MiB
Duration                                 : 1mn 52s
Overall bit rate mode                    : Variable
Overall bit rate                         : 687 Kbps
Movie name                               : Formula 1 (160x128)
Encoded date                             : UTC 2011-01-25 09:03:17
Tagged date                              : UTC 2011-01-25 09:03:17
Writing application                      : VirtualDubMod 1.6.0.0 SURROUND (build 2560/release)

Video
ID                                       : 2
Format                                   : JPEG
Codec ID                                 : jpeg
Duration                                 : 1mn 52s
Bit rate mode                            : Variable
Bit rate                                 : 507 Kbps
Width                                    : 160 pixels
Height                                   : 128 pixels
Display aspect ratio                     : 5:4
Frame rate mode                          : Constant
Frame rate                               : 24.000 fps
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 1.032
Stream size                              : 6.78 MiB (74%)
Language                                 : English
Encoded date                             : UTC 2011-01-25 09:03:17
Tagged date                              : UTC 2011-01-25 09:03:17

Audio
ID                                       : 1
Format                                   : ADPCM
Codec ID                                 : 11
Codec ID/Hint                            : Intel
Duration                                 : 1mn 51s
Bit rate mode                            : Constant
Bit rate                                 : 176.4 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 22.05 KHz
Stream size                              : 2.35 MiB (26%)
Language                                 : English
Encoded date                             : UTC 2011-01-25 09:03:17
Tagged date                              : UTC 2011-01-25 09:03:17


```

---

### Post by ron999 on 2011-12-28
> **CarlWalters said:**
> 
[mp4 @ 0x8f22ac0] track 1: could not find tag, codec not currently supported in container

Hi
I think FFmpeg is complaining that audio codec "adpcm_ima_wav" isn't supported in mp4 container.
Try running your command with **-an** like this:-
```
ffmpeg -i tmp.mp4 -s 128x128 -vcodec mjpeg -an output.mp4
```

See what the result looks like and whether it plays in the GoGear.
Then experiment with other audio codecs later.

---

### Post by CarlWalters on 2011-12-29
Many thanks for all the help. I think I have a working solution now courtesy of someone on the Philips support forum :D

```

#!/bin/sh
# GoGearVibeConvert.sh - converts videos to be played on Philips GoGear Vibe

[ "x$1" != "x" ] || { echo "usage: $(basename $0) <input file>" 1>&2; exit 1; }

ffmpeg -i "$1" \
  -f mov \
  -vcodec mjpeg -s 160x128 -b 512k -r 25 \
  -acodec adpcm_ima_wav -ab 192k -ar 22050 \
  -metadata title="${1}.mp4" \
  "${1}.mp4"

```

---

### Post by ron999 on 2011-12-29
> **CarlWalters said:**
> I think I have a working solution now ...
Yes, using "-f mov" has allowed FFmpeg to accept the adpcm_ima_wav codec.:)

---

### Post by dvandok on 2012-05-14
> **CarlWalters said:**
> Many thanks for all the help. I think I have a working solution now courtesy of someone on the Philips support forum :D

This worked in 11.10, but stopped working for me in 12.04 (the player would say 'file format not supported' or something along those lines) which seems to relate to the transition to avconv over ffmpeg. I followed these guidelines:  [http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) and I got it back to work again.

Thanks!

---

### Post by boardman on 2012-10-19
I bought a Philips GoGear SA060 for my son and had problems getting the video playback on the GoGear but I managed to get handbrake to encode video in a format the GoGear can read. Philips Support were very polite and friendly but their knowldege only extends as far as the instruction manual.

The solution I got working was:

1. Download and install Handbrake ([http://handbrake.fr]("http://handbrake.fr"))
2. Load the source file
3. choose an output filename (handbrake will make it end in .m4v)
4. Select the "ipod" preset
5. In the Video tab:
[INDENT]change the framerate to 25
select peak frame rate (VFR)
select "constant quality" and set it to 25
[/INDENT]
6. In the audio tab:
[INDENT]select the AAC(faac) codec
set mix to stereo[/INDENT]
7. Click on the picture settings button in the menu at the top of the screen. You can change the video size here. I left it at 320x176 for my test video and it looked great, possibly you can get away with making it even smaller. As far as I can tell the screen resolution for the GoGear is 480x320 so anything larger than this is a waste of data.
8. Click add to que
9. Click start
10. wait.
11. once it is finished change the file extension FROM ".m4v" TO ".mp4" or else the GoGear will not see it.
12. copy the file to the VIDEO folder
13. sometimes I have to restart the goGear before I can play the file but not always.

My 12 minute video was 34 odd megabytes after converting.

The above settings are not 'written in stone'. The 'universal' preset also worked. Just check the framerate is 25 and picture size is less than 720x476. At larger picture sizes the Mbps limit may catch you out so I'd tend to aim for the max of 480x320 anyway. Once I got the video working I had to play a little to get sound working.

At any rate this is a good starting point that you can tinker with.

I registered here and left these notes as this thread came up when I was looking for how to make the video work.

---

### Post by madoshwa on 2012-12-25
Another, rather unorthodox way, of doing this, is to put a virtual machine of xp/vista/7 on your computer. install songbird. make sure the extras are installed from the site, and that you have the guest account installed. then just connect your mp3 player, put the video over, and it converts it for you. it takes a little longer, but its what i did for my gogear :)

---

