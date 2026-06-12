---
title: "How to convert AVCHD (MTS/M2TS) to MP4 losslessly."
date: 2010-09-11
forum: Multimedia Software
---

### Post by pHr34kY on 2010-09-11
I'll start with the end:

```
mencoder infile.mts -demuxer lavf -oac copy -ovc copy -of lavf=mp4 -o outfile.mp4
```

..and now to explain myself:

AVCHD (MTS) is basically a container format for MPEG4-AVC video and AC-3 Audio. It's commonly found on modern camcorders. I have pulled files off a Sony Camcorder (I forget which model), which records in 1080i@50Hz. It seems there are timestamp problems, and both the even and odd fields are stamped with the same time, and not 1/50th of a second apart as you'd expect. This currently breaks ffmpeg (0.6~svn20100711), and the mencoder (SVN-r31722) internal demuxer doesn't like it either. The libavformat (lavf 0.6~svn20100711) demuxer/muxer seems to handle it, so that's what we'll use.

If you run 'mediainfo' over an MTS file, you'll see something like this:

```
General
ID                               : 0
Complete name                    : infile.mts
Format                           : BDAV
Format/Info                      : Blu-ray Video
File size                        : 62.6 MiB
Duration                         : 56s 72ms
Overall bit rate                 : 9 364 Kbps
Maximum Overall bit rate         : 18.0 Mbps

Video
ID                               : 4113 (0x1011)
Menu ID                          : 1 (0x1)
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 2 frames
Duration                         : 56s 0ms
Bit rate                         : 8 726 Kbps
Width                            : 1 440 pixels
Height                           : 1 080 pixels
Display aspect ratio             : 16:9
Frame rate                       : 25.000 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Interlaced
Scan order                       : Top Field First
Bits/(Pixel*Frame)               : 0.224
Stream size                      : 58.3 MiB (93%)

Audio
ID                               : 4352 (0x1100)
Menu ID                          : 1 (0x1)
Format                           : AC-3
Format/Info                      : Audio Coding 3
Duration                         : 56s 128ms
Bit rate mode                    : Constant
Bit rate                         : 256 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 48.0 KHz
Video delay                      : -80ms
Stream size                      : 1.71 MiB (3%)

Text
ID                               : 4608 (0x1200)
Menu ID                          : 1 (0x1)
Format                           : PGS
Duration                         : 55s 575ms
Video delay                      : -80ms
```


Once you run it through the above command, the resultant container will look like this. The audio/video codec details will be the same because it's a straight (lossless) copy. Also note that the headers have been corrected from 25i to 50i.

```
General
Complete name                    : outfile.mp4
Format                           : MPEG-4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 58.7 MiB
Duration                         : 56s 160ms
Overall bit rate                 : 8 761 Kbps
Writing application              : Lavf52.73.0

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 2 frames
Format_Settings_FrameMode        : Frame tripling
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 56s 140ms
Bit rate mode                    : Variable
Bit rate                         : 8 504 Kbps
Width                            : 1 440 pixels
Height                           : 1 080 pixels
Display aspect ratio             : 4:3
Original display aspect ratio    : 16:9
Frame rate mode                  : Constant
Frame rate                       : 50.000 fps
Original frame rate              : 8.333 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Interlaced
Scan order                       : Top Field First
Bits/(Pixel*Frame)               : 0.109
Stream size                      : 56.9 MiB (97%)

Audio
ID                               : 2
Format                           : AC-3
Format/Info                      : Audio Coding 3
Codec ID                         : ac-3
Duration                         : 56s 160ms
Bit rate mode                    : Constant
Bit rate                         : 256 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Stream size                      : 1.71 MiB (3%)

```

Note that the final video will still be interlaced. Removing the interlacing requires re-encoding.

This was tested on 10.04 with the VDPAU team's cutting-edge-multimedia PPA installed.

---

### Post by excetara2 on 2010-09-14
I want to do this on files from a canon hg-21. Here is my output from mediainfo:


General
ID                               : 0
Complete name                    : 00069.MTS
Format                           : BDAV
Format/Info                      : BluRay Video
File size                        : 272 MiB
Duration                         : 1mn 36s
Overall bit rate                 : 23.8 Mbps
Maximum Overall bit rate         : 24.0 Mbps

Video
ID                               : 4113 (0x1011)
Menu ID                          : 1 (0x1)
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 2 frames
Duration                         : 1mn 35s
Bit rate                         : 22.6 Mbps
Width                            : 1 920 pixels
Height                           : 1 080 pixels
Display aspect ratio             : 16/9
Frame rate                       : 29.970 fps
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Interlaced
Scan order                       : Top Field First
Bits/(Pixel*Frame)               : 0.363

Audio
ID                               : 4352 (0x1100)
Menu ID                          : 1 (0x1)
Format                           : AC-3
Format/Info                      : Audio Coding 3
Duration                         : 1mn 36s
Bit rate mode                    : Constant
Bit rate                         : 256 Kbps
Channel(s)                       : 2 channels
Channel positions                : L R
Sampling rate                    : 48.0 KHz
Video delay                      : -66ms


This is after conversion:


General
Complete name                    : RyanFreakout.mp4
Format                           : MPEG-4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 260 MiB
Duration                         : 1mn 36s
Overall bit rate                 : 22.7 Mbps
Encoded date                     : UTC 1970-01-01 00:00:00
Tagged date                      : UTC 1970-01-01 00:00:00
Writing application              : Lavf52.31.0

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 2 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 1mn 36s
Bit rate mode                    : Variable
Bit rate                         : 22.4 Mbps
Width                            : 1 920 pixels
Height                           : 1 080 pixels
Display aspect ratio             : 16/9
Frame rate mode                  : Constant
Frame rate                       : 59.940 fps
Original frame rate              : 29.970 fps
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.181
Stream size                      : 257 MiB (99%)
Encoded date                     : UTC 1970-01-01 00:00:00
Tagged date                      : UTC 1970-01-01 00:00:00

Audio
Format                           : AC-3
Format/Info                      : Audio Coding 3
Codec ID                         : ac-3
Duration                         : 1mn 36s
Bit rate mode                    : Constant
Bit rate                         : 256 Kbps
Channel(s)                       : 2 channels
Channel positions                : L R
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Stream size                      : 2.93 MiB (1%)
Encoded date                     : UTC 1970-01-01 00:00:00
Tagged date                      : UTC 1970-01-01 00:00:00


Does everything look right? The playback on .mp4 is still obviously interlaced but it seems to be worse than before. When usually I get better playback. Previously, I had always used Adobe Media Encoder on Windows (deinterlaces the file). Can I deinterlace this file (reencode with mencoder)? Are my settings right for converting this like yours?

Cheers

---

### Post by webdevelopment on 2010-09-17
looking to convert MTS into a usable format too...

WinFF gives this error when trying to convert MTS files:

Input #0, mpegts, from '/home/admin1/Pictures/AVCHD/BDMV/STREAM/00000.MTS':
  Duration: 00:04:56.32, start: 1.000067, bitrate: 17173 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, stereo, s16, 256 kb/s
Unknown encoder 'libmp3lame'
Press Enter to Continue

---

### Post by andrew.46 on 2010-09-17
Hi web,

> **webdevelopment said:**
> 
```
Unknown encoder 'libmp3lame'
```


Looks like your copy of FFmpeg has not been compiled for mp3 encoding, have a look here for the fix:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Andrew

---

### Post by webdevelopment on 2010-09-17
> **andrew.46 said:**
> Hi web,



Looks like your copy of FFmpeg has not been compiled for mp3 encoding, have a look here for the fix:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Andrew

thanks!

this worked...

solution was to download winff then install the medibuntu codecs

but i converted to mp4 and the output is only 15fps (using winff)

i'm almost certain the source vidoe is 30fps 1080p HD video...

how do i get a better output? (i guess the term is lossless?) 

i'd like the highest quality source that i can use from the MTS files...

---

### Post by ron999 on 2010-09-17
Use MediaInfo to show your before and after files.

---

### Post by webdevelopment on 2010-09-17
> **ron999 said:**
> Use MediaInfo to show your before and after files.

where do i get this? its not in my synaptec installer

---

### Post by webdevelopment on 2010-09-17
download mediainfo from their site now it requires libmediainfo0 which is not easy to find... this is down the rabbit hole of crappy linux stuff

---

### Post by webdevelopment on 2010-10-01
winff to convert MTS (sony HD cam) to MPEG4 but it's giving me an output of 15 frames per second even though my source video files are 30 frames per second...

how do i fix this?

also, whats the best and easiest video editor for MTS/mpeg4 1080p files?  i just need to put in some titles and cut/splice out unwanted video scenes, but i need a video editor that wont crash.

---

### Post by webdevelopment on 2010-10-01
how do i change this to preserve the original dimensions, bitrate, and fps?  i tried entering 30fps in the additional options in WinFF but it ignored them as you can see below and converted my HD video at a 704x384 size and lower bitrate and lower fps...

> FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2  --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau  --enable-bzlib --enable-libgsm --enable-libschroedinger  --enable-libspeex --enable-libtheora --enable-libvorbis  --enable-pthreads --enable-zlib --disable-stripping --disable-vhook  --enable-gpl --enable-postproc --enable-swscale --enable-x11grab  --enable-libdc1394  --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include  --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
Input #0, mpegts, from '/home/admin1/Pictures/00031.MTS':
  Duration: 00:01:41.63, start: 1.000067, bitrate: 17131 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, stereo, s16, 256 kb/s
Output #0, mp4, to '/home/admin1/00031.mp4':
    Stream #0.0: Video: libx264, yuv420p, 704x384 [PAR 32:33 DAR 16:9], q=10-51, 1250 kb/s, 90k tbn, 30 tbc
    Stream #0.1: Audio: libfaac, 48000 Hz, stereo, s16, 112 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x1f50d40]using SAR=32/33
[libx264 @ 0x1f50d40]using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x1f50d40]profile Main, level 3.0
Press [q] to stop encoding
frame= 1938 fps=  9 q=22.0 Lsize=   10753kB time=63.87 bitrate=1379.2kbits/s    
video:9836kB audio:872kB global headers:1kB muxing overhead 0.415946%
[libx264 @ 0x1f50d40]slice I:621   Avg QP:24.70  size:  5383
[libx264 @ 0x1f50d40]slice P:378   Avg QP:20.23  size:  9592
[libx264 @ 0x1f50d40]slice B:939   Avg QP:21.61  size:  3305
[libx264 @ 0x1f50d40]consecutive B-frames:  4.3%  1.5%  0.9% 93.2%
[libx264 @ 0x1f50d40]mb I  I16..4: 72.7%  0.0% 27.3%
[libx264 @ 0x1f50d40]mb P  I16..4: 14.6%  0.0% 13.6%  P16..4: 39.8% 18.1% 10.5%  0.0%  0.0%    skip: 3.3%
[libx264 @ 0x1f50d40]mb B  I16..4:  2.2%  0.0%  1.1%  B16..8: 65.5%   2.1%  5.3%  direct: 2.3%  skip:21.5%  L0:37.7% L1:53.0% BI: 9.3%
[libx264 @ 0x1f50d40]coded y,uvDC,uvAC intra:65.8% 72.6% 23.4% inter:18.2% 42.4% 2.7%
[libx264 @ 0x1f50d40]SSIM Mean Y:0.9571350
[libx264 @ 0x1f50d40]kb/s:1247.3
Press Enter to Continue

---

### Post by FakeOutdoorsman on 2010-10-01
You can use FFmpeg directly to copy the video and audio into a MP4 container:
```
ffmpeg -i 00031.MTS -vcodec copy -acodec copy output.mp4
```
You can then combine this with *find* to do a batch type conversion:

[Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937)

Or you could make a new WinFF preset based on my example.

---

### Post by webdevelopment on 2010-10-01
here is the mpeg4 preset in WinFF

> <?xml version="1.0"?>
<presets>
  <x264HQWS>
    <label>MP4 Widescreen</label>
    <params>-f mp4 -r 29.97 -vcodec libx264 -s 704x384 -b 1000kb -aspect 16:9 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1250k -maxrate 1500k -bufsize 4M -bt 256k -refs 1 -bf 3 -coder 1 -me_method umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8+partb8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec libfaac -ab 112kb -ar 48000 -ac 2</params>
    <extension>mp4</extension>
    <category>MPEG4</category>
  </x264HQWS>
</presets>

where can i find one that is for 1080p HD MPEG4?

---

### Post by control_guy on 2010-11-18
Very good post. Very useful. It solved one of my problems. Now my question is how do you include the text stream as well, the PGS?

Thanks

> **pHr34kY said:**
> I'll start with the end:

```
mencoder infile.mts -demuxer lavf -oac copy -ovc copy -of lavf=mp4 -o outfile.mp4
```

..

---

### Post by whytenoiz on 2012-06-01
How would you adapt your command for a media info output such as :

$ mediainfo 00047.MTS
General
ID                                       : 0 (0x0)
Complete name                            : 00047.MTS
Format                                   : BDAV
Format/Info                              : Blu-ray Video
File size                                : 25.8 MiB
Duration                                 : 20s 974ms
Overall bit rate mode                    : Variable
Overall bit rate                         : 10.3 Mbps
Maximum Overall bit rate                 : 18.0 Mbps

Video
ID                                       : 4113 (0x1011)
Menu ID                                  : 1 (0x1)
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 2 frames
Format settings, GOP                     : M=2, N=15
Codec ID                                 : 27
Duration                                 : 20s 954ms
Bit rate mode                            : Variable
Bit rate                                 : 9 432 Kbps
Maximum bit rate                         : 16.0 Mbps
Width                                    : 1 440 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Top Field First
Bits/(Pixel*Frame)                       : 0.202
Stream size                              : 23.6 MiB (91%)

Audio
ID                                       : 4352 (0x1100)
Menu ID                                  : 1 (0x1)
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Codec ID                                 : 129
Duration                                 : 21s 24ms
Bit rate mode                            : Constant
Bit rate                                 : 448 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Delay relative to video                  : -67ms
Stream size                              : 1.12 MiB (4%)

Text
ID                                       : 4608 (0x1200)
Menu ID                                  : 1 (0x1)
Format                                   : PGS
Codec ID                                 : 144
Duration                                 : 20s 455ms
Delay relative to video                  : -67ms

---

### Post by alvgarci on 2012-12-09
Hi:

This is indeed a very useful thread. I was working a lot on a smooth way to convert MTS to a more useful mp4 container without recompress it (loosely). I use for it ffmpeg.. and I correct timestamp issues.. but I couldn't fix the issue on converting to mp4 AC3 5.1..

let's take video 1 (MTS format). This is what mediainfo says:

General
ID                                       : 0 (0x0)
Complete name                            : 1.MTS
Format                                   : BDAV
Format/Info                              : Blu-ray Video
File size                                : 96.3 MiB
Duration                                 : 47s 287ms
Overall bit rate mode                    : Variable
Overall bit rate                         : 17.1 Mbps
Maximum Overall bit rate                 : 18.0 Mbps

Video
ID                                       : 4113 (0x1011)
Menu ID                                  : 1 (0x1)
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 2 frames
Format settings, GOP                     : M=2, N=15
Codec ID                                 : 27
Duration                                 : 46s 480ms
Bit rate mode                            : Variable
Bit rate                                 : 16.0 Mbps
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Top Field First
Bits/(Pixel*Frame)                       : 0.257
Stream size                              : 88.3 MiB (92%)

Audio
ID                                       : 4352 (0x1100)
Menu ID                                  : 1 (0x1)
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Format settings, Endianness              : Big
Codec ID                                 : 129
Duration                                 : 46s 560ms
Bit rate mode                            : Constant
Bit rate                                 : 448 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 2.49 MiB (3%)

Text
ID                                       : 4608 (0x1200)
Menu ID                                  : 1 (0x1)
Format                                   : PGS
Codec ID                                 : 144
Duration                                 : 45s 981ms

ok.. 6 channels..

so I run my ffmpeg command on a batch:

for f in *.MTS

do 

    DATE=$(exiftool-5.12 -d "%Y-%m-%d %H:%M:%S"  "$f" | grep Date.*Original | awk '{print $4, $5;}')


    ffmpeg -i  "$f" -y -acodec copy -vcodec copy  -f mp4 -metadata creation_time="$DATE" "./original/${f%.MTS}.MP4"


done


Here is the mediainfo output of the MP4...

General
Complete name                            : 1.MP4
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 91.2 MiB
Duration                                 : 46s 560ms
Overall bit rate mode                    : Variable
Overall bit rate                         : 16.4 Mbps
Encoded date                             : UTC 2012-10-27 11:07:24
Tagged date                              : UTC 2012-10-27 11:07:24
Writing application                      : Lavf54.29.104

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 2 frames
Format settings, GOP                     : M=2, N=15
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 46s 547ms
Bit rate mode                            : Variable
Bit rate                                 : 16.0 Mbps
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Variable
Frame rate                               : 59.940 fps
Original frame rate                      : 29.970 fps
Minimum frame rate                       : 59.920 fps
Maximum frame rate                       : 59.960 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Top Field First
Bits/(Pixel*Frame)                       : 0.129
Stream size                              : 88.6 MiB (97%)
Encoded date                             : UTC 2012-10-27 11:07:24
Tagged date                              : UTC 2012-10-27 11:07:24

Audio
ID                                       : 2
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Format settings, Endianness              : Big
Codec ID                                 : ac-3
Duration                                 : 46s 560ms
Bit rate mode                            : Constant
Bit rate                                 : 448 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 2.49 MiB (3%)
Encoded date                             : UTC 2012-10-27 11:07:24
Tagged date                              : UTC 2012-10-27 11:07:24

but Exiftool said:

ExifTool Version Number         : 9.06
File Name                       : 1.MP4
Directory                       : .
File Size                       : 91 MB
File Modification Date/Time     : 2012:12:10 02:12:46+01:00
File Access Date/Time           : 2012:12:10 02:14:25+01:00
File Permissions                : rw-r--r--
File Type                       : MP4
MIME Type                       : video/mp4
Major Brand                     : MP4  Base Media v1 [IS0 14496-12:2003]
Minor Version                   : 0.2.0
Compatible Brands               : isom, iso2, avc1, mp41
Movie Data Size                 : 95557281
Movie Header Version            : 0
Create Date                     : 2012:10:27 11:07:24
Modify Date                     : 2012:10:27 11:07:24
Time Scale                      : 1000
Duration                        : 0:00:46
Preferred Rate                  : 1
Preferred Volume                : 100.00%
Preview Time                    : 0 s
Preview Duration                : 0 s
Poster Time                     : 0 s
Selection Time                  : 0 s
Selection Duration              : 0 s
Current Time                    : 0 s
Next Track ID                   : 3
Track Header Version            : 0
Track Create Date               : 2012:10:27 11:07:24
Track Modify Date               : 2012:10:27 11:07:24
Track ID                        : 1
Track Duration                  : 0:00:46
Track Layer                     : 0
Track Volume                    : 0.00%
Image Width                     : 1920
Image Height                    : 1080
Graphics Mode                   : srcCopy
Op Color                        : 0 0 0
Compressor ID                   : avc1
Source Image Width              : 1920
Source Image Height             : 1080
X Resolution                    : 72
Y Resolution                    : 72
Bit Depth                       : 24
Video Frame Rate                : 59.94
Matrix Structure                : 1 0 0 0 1 0 0 0 1
Media Header Version            : 0
Media Create Date               : 2012:10:27 11:07:24
Media Modify Date               : 2012:10:27 11:07:24
Media Time Scale                : 48000
Media Duration                  : 0:00:46
Media Language Code             : und
Handler Description             : SoundHandler
Balance                         : 0
Audio Channels                  : 2
Audio Bits Per Sample           : 16
Audio Sample Rate               : 48000
Handler Type                    : Metadata
Handler Vendor ID               : Apple
Encoder                         : Lavf54.29.104
Avg Bitrate                     : 16.4 Mbps
Image Size                      : 1920x1080
Rotation                        : 0

So... I lost 3 audio channels :-(.. on exiftool but mediainfo gaves me a perfect conversion...

how can I be sure that I have a loosely audio and video MP4 file? which of them lies?


Any help?

Thanks

---

### Post by Merrattic on 2012-12-15
My problem on converting mts files and re-encoding them (say for example I have 4 x 4gb MTS files with a 1.5 hour runtime in total, and these need to be encoded to fit on a DVD). All attempts whether directly using ffmpeg (compiled) or WinFF or on W7 DVD Flick or winff result in an audio delay.

Now I normally get an a/v delay if I try to encode ts files from my dvb stick. I get round this by demuxing them using ProjectX then encdoing the video and audio separately before muxing them back together. However ProjectX won't demux my mts files :(

Is there a fix in ffmpeg for this a/v delay (Video is running slightly behind audio, at the same gap throughout the encode - e.g. it doesn't get worse as time progresses.....

---

### Post by BicyclerBoy on 2012-12-15
m2ts & mpeg-ts files have PTS presentation time stamps for all streams.
It is normal for dvb OTA mpegts to have 2 seconds delay between video & audio so the decoder can handle out-of-order video encoding & post process video.

I don't have any a/v sync problems using ffmpeg on with mpegts files for selective stream transcoding/removal. I just use mpeg(2)-ts output container
-f mpegts

If you convert these to a deprecated container like AVI then you get a/v sync problems.
I believe you have to fine-tune the a/v sync with ‘-delay[:stream_specifier] integer ()’ to find a solution for your DVD player & use constant bitrate & packed B frames etc.

If you are remuxing into mkv or mpeg4 container then this could help:
-vsync passthrough -copyts

---

### Post by Merrattic on 2012-12-17
Thanks Bicycler Boy, useful info.

Using -f mpegts as an output will mean no encoding or reduction in filesize I am guessing? (Hence no problem with A/V sync ;))

I've got to get from 16GB of video down to 4.3Gb :(

---

### Post by BicyclerBoy on 2012-12-17
Most of what I just posted is of little use here..

The transport stream formats have 10%-20% overhead (over PS) but can be cut & joined & seeked at random.

The PS & TS & mkv containers have audio & video packet timing info.

Problems start when trying to stuff modern video codecs into AVI container as it does not have adequate timing info. It needs constant frame rate & bitrates & lots of stuffing tricks to allow out-of-order frames.

Are you trying to make a DVD-video (mpeg2 PS VOB) or *.avi (DVD data)?

The AVI method could let you to use DivX compression.

---

### Post by Merrattic on 2012-12-18
Seems OK now, found that outputting to -target pal-dvd gives good a/v sync and the right file size

---

### Post by FakeOutdoorsman on 2012-12-18
> **Merrattic said:**
> All attempts whether directly using ffmpeg (compiled) or WinFF or on W7 DVD Flick or winff result in an audio delay.

What was your (compiled) ffmpeg command? I'm just curious since you solved the issue.

---

### Post by Merrattic on 2012-12-18
Really nothing special (just testing at present, seeking a/v sync goodness before tweaking any further)
```
ffmpeg -i input.MTS -t 30 -target pal-dvd -aspect 16:9 output.mpg
```This encodes a 30 second segment from @ 80mb down to @20mb, with good enough quality for large screen output. This on Xubuntu 12.04 using a Dell Precision M6500 laptop (well, desktop replacement ;) ) Yet to run it on a full 23 minutes of MTS (4GB segment) to see if A/V sync remains OK all the way through.

Any advice on improving the line is always welcome :)

EDIT run the line on a full 4GB, and no a/v sync problems. Will have to see what happens when I author the DVD ;)

EDIT have been using DVD Flick on W7 to create dvd isos, but this just puts the a/v sync problem back, even without re-encoding the video, so installed DEVEDE and got a perfect dvd iso, with menu :)

---

