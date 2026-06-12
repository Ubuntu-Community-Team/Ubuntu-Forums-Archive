---
title: "Sansa Fuse video projects?"
date: 2009-03-10
forum: Multimedia Software
---

### Post by cptrohn on 2009-03-10
Hi I have a Sansa Fuse and am having a very hard time getting video to the player... It uses a windows program called Sansa Media converter and it appears this is the only way to properly convert the video so the PMP will recognize it that I have found... I tried the Sansa support forums, but the vast majority of anybody I have talked with there are windows users.. (and apperently they are having lots of problems with this as well)

I was just wondering if there were any current linux/ubuntu projects maybe going on to perhaps address this issue since Sansa is advertising this as fully linux compatible.... I can get music to go with drag and drop no problem at all...

But the video is just not happening for me at this time...  I tried to ask on their forum about codecs and other settings etc for possibly using handbrake to convert the video but nobody there really seems to know about it..... I know when I was a windows user and had a Zune I had to use 3rd party software to convert video for Zune... I was just wondering if anybody knew of a linux package that would do the same for the Fuse?

---

### Post by cptrohn on 2009-03-10
I found this posted in a forum that is supposed to be the video output of the default video that comes with the player.


[http://www.anythingbutipod.com/forum/showthread.php?t=27460](http://www.anythingbutipod.com/forum/showthread.php?t=27460)

---

### Post by FakeOutdoorsman on 2009-03-10
Here's a command for FFmpeg that loosely following the specs linked above.  Does this work?  Assuming you're using intrpeid:
```
ffmpeg -i inputvideo.mp4 -acodec libmp3lame -ab 128k -ar 44100 -vcodec mpeg4 -b 512k -s 224x176 output.avi
```
or:
```
ffmpeg -i inputvideo.mp4 -acodec libmp3lame -ab 128k -ar 44100 -vcodec libxvid -b 512k -s 224x176 output.avi
```
You will need the **libavcodec-unstripped-51** package to enable restricted encoders in FFmpeg (Intrepid only).

---

### Post by vgay on 2009-05-22
> **FakeOutdoorsman said:**
> Here's a command for FFmpeg that loosely following the specs linked above.  Does this work?  Assuming you're using intrpeid:
```
ffmpeg -i inputvideo.mp4 -acodec libmp3lame -ab 128k -ar 44100 -vcodec mpeg4 -b 512k -s 224x176 output.avi
```or:
```
ffmpeg -i inputvideo.mp4 -acodec libmp3lame -ab 128k -ar 44100 -vcodec libxvid -b 512k -s 224x176 output.avi
```You will need the **libavcodec-unstripped-51** package to enable restricted encoders in FFmpeg (Intrepid only).

hi,

I bought this mp3 player a couple of weeks ago and everything works fine except the video

I enjoyed to find your solution but... no success :(

The additional difficulty for me is that I have not Windows and that Sansa Media Converter does not work with wine, so I'm unable to analyse what the file is, converted by this proprietary software. And I'm not really an expert with ffmpeg ;-)

Did anybody else ear about a (working) solution ?
 
I'll try again next week

Vincent

P.S. my apologies for my poor English

---

### Post by FakeOutdoorsman on 2009-05-24
> **vgay said:**
> hi,

I bought this mp3 player a couple of weeks ago and everything works fine except the video

I enjoyed to find your solution but... no success :(

The additional difficulty for me is that I have not Windows and that Sansa Media Converter does not work with wine, so I'm unable to analyse what the file is, converted by this proprietary software. And I'm not really an expert with ffmpeg ;-)

Did anybody else ear about a (working) solution ?
 
I'll try again next week

Vincent

P.S. my apologies for my poor English

Your English is not poor.  Do you have a video that does work on this player?  We can use it to determine a working format.  If you do have a working video you can use [mediainfo](http://mediainfo.sourceforge.net/en/Download/Ubuntu) to get the file statistics.  I can then attempt to provide a FFmpeg command.  Example mediainfo command:
```
mediainfo test.mp4
```

---

### Post by vgay on 2009-05-30
> **FakeOutdoorsman said:**
>  Do you have a video that does work on this player?  We can use it to determine a working format.  If you do have a working video you can use [mediainfo]("http://mediainfo.sourceforge.net/en/Download/Ubuntu") to get the file statistics.  I can then attempt to provide a FFmpeg command. 

Many thanks for your help

I've installed XP with virtualbox, then used the proprietary program supplied by Sanza. This program produced a avi film (working fine on the Sansa Fuze) and a jpeg picture with .thm extension. 

What does not appear with mediainfo, but indicated on sansa site, is that the format of video must be "mpeg-4 simple profile". I don't exactly know what it means, excepted what I found on Wikipedia ( [http://en.wikipedia.org/wiki/MPEG-4_Part_2](http://en.wikipedia.org/wiki/MPEG-4_Part_2) )

> **Simple Profile** is mostly aimed for use in situations where low bit rate and low resolution are mandated by other conditions of the applications, like network bandwidth, device size etc. Examples are cell phones, some low end video conferencing systems, surveillance systems etc.--- mediainfo result for mediainfo -f 15619157.avi ---

General
Count                            : 257
Count of stream of this kind     : 1
Kind of stream                   : General
Kind of stream                   : General
Stream identifier                : 0
Count of video streams           : 1
Count of audio streams           : 1
Video_Format_List                : MPEG-4 Visual
Video_Format_WithHint_List       : MPEG-4 Visual (DivX 5)
Codecs Video                     : DivX 5
Audio_Format_List                : MPEG Audio
Audio_Format_WithHint_List       : MPEG Audio (MP3)
Audio codecs                     : MPEG-1 Audio layer 3
Complete name                    : /media/SANSA FUZE/VIDEO/15619157.avi
Folder name                      : /media/SANSA FUZE/VIDEO
File name                        : 15619157
File extension                   : avi
Format                           : AVI
Format                           : AVI
Format/Info                      : Audio Video Interleave
Format/Extensions usually used   : avi
Interleaved                      : Yes
Codec                            : AVI
Codec                            : AVI
Codec/Info                       : Audio Video Interleave
Codec/Extensions usually used    : avi
File size                        : 44671778
File size                        : 42.6 MiB
File size                        : 43 MiB
File size                        : 43 MiB
File size                        : 42.6 MiB
File size                        : 42.60 MiB
Duration                         : 438050
Duration                         : 7mn 18s
Duration                         : 7mn 18s 50ms
Duration                         : 7mn 18s
Duration                         : 00:07:18.050
Overall bit rate                 : 815829
Overall bit rate                 : 816 Kbps
Stream size                      : 544722
Stream size                      : 532 KiB (1%)
Stream size                      : 532 KiB
Stream size                      : 532 KiB
Stream size                      : 532 KiB
Stream size                      : 532.0 KiB
Stream size                      : 532 KiB (1%)
Proportion of this stream        : 0.01219
Writing application              : InterVideo

Video
Count                            : 144
Count of stream of this kind     : 1
Kind of stream                   : Video
Kind of stream                   : Video
Stream identifier                : 0
Format                           : MPEG-4 Visual
Format settings                  : BVOP
Format settings, BVOP            : Yes
Format settings, BVOP            : Yes
Format settings, QPel            : No
Format settings, QPel            : No
Format settings, GMC             : 0
Format settings, GMC             : No warppoints
Format settings, Matrix          : Default (H.263)
Format settings, Matrix          : Default (H.263)
Codec ID                         : DX50
Codec ID/Hint                    : DivX 5
Codec ID/Url                     : [http://mediaarea.net/DX50](http://mediaarea.net/DX50)
Codec                            : DX50
Codec                            : DivX 5
Codec/Family                     : MPEG-4V
Codec/Url                        : [http://www.divx.com](http://www.divx.com)
Codec/CC                         : DX50
Codec settings                   : BVOP
Codec settings, Packet bitstream : No
Codec settings, BVOP             : Yes
Codec settings, QPel             : No
Codec settings, GMC              : 0
Codec settings, GMC              : No warppoints
Codec settings, Matrix           : Default (H.263)
Duration                         : 438050
Duration                         : 7mn 18s
Duration                         : 7mn 18s 50ms
Duration                         : 7mn 18s
Duration                         : 00:07:18.050
Bit rate                         : 677905
Bit rate                         : 678 Kbps
Width                            : 224
Width                            : 224 pixels
Height                           : 176
Height                           : 176 pixels
Pixel aspect ratio               : 1.000
Display aspect ratio             : 1.273
Display aspect ratio             : 1.273
Frame rate                       : 20.000
Frame rate                       : 20.000 fps
Frame count                      : 8761
Resolution                       : 24
Resolution                       : 24 bits
Scan type                        : Progressive
Scan type                        : Progressive
Interlacement                    : PPF
Interlacement                    : Progressive
Bits/(Pixel*Frame)               : 0.860
Delay                            : 0
Stream size                      : 37119553
Stream size                      : 35.4 MiB (83%)
Stream size                      : 35 MiB
Stream size                      : 35 MiB
Stream size                      : 35.4 MiB
Stream size                      : 35.40 MiB
Stream size                      : 35.4 MiB (83%)
Proportion of this stream        : 0.83094

Audio
Count                            : 122
Count of stream of this kind     : 1
Kind of stream                   : Audio
Kind of stream                   : Audio
Stream identifier                : 0
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Format settings                  : Dual mono
Codec ID                         : 55
Codec ID/Hint                    : MP3
Codec ID/Url                     : [http://www.iis.fraunhofer.de/amm/index.html](http://www.iis.fraunhofer.de/amm/index.html)
Codec                            : MPA1L3
Codec                            : MPEG-1 Audio layer 3
Codec/CC                         : 55
Codec profile                    : Dual mono
Duration                         : 437969
Duration                         : 7mn 17s
Duration                         : 7mn 17s 969ms
Duration                         : 7mn 17s
Duration                         : 00:07:17.969
Bit rate mode                    : CBR
Bit rate mode                    : Constant
Bit rate                         : 128000
Bit rate                         : 128 Kbps
Channel(s)                       : 2
Channel(s)                       : 2 channels
Sampling rate                    : 44100
Sampling rate                    : 44.1 KHz
SamplingCount                    : 19314433
Resolution                       : 16
Resolution                       : 16 bits
Delay                            : 0
Video delay                      : 0
Video0 delay                     : 0
Stream size                      : 7007503
Stream size                      : 6.68 MiB (16%)
Stream size                      : 7 MiB
Stream size                      : 6.7 MiB
Stream size                      : 6.68 MiB
Stream size                      : 6.683 MiB
Stream size                      : 6.68 MiB (16%)
Proportion of this stream        : 0.15687
Alignment                        : Split
Alignment                        : Split accross interleaves
Interleave, duration             : 2.00
Interleave, duration             : 100
Interleave, duration             : 100 ms (2.00 video frames)

--- end of mediainfo result ---

--- mediainfo result for mediainfo -f 15619157.thm ---

General
Count                            : 257
Count of stream of this kind     : 1
Kind of stream                   : General
Kind of stream                   : General
Stream identifier                : 0
Count of image streams           : 1
Image_Format_List                : JPEG
Image_Format_WithHint_List       : JPEG
Codecs Image                     : JPEG
Complete name                    : /media/SANSA FUZE/VIDEO/15619157.thm
Folder name                      : /media/SANSA FUZE/VIDEO
File name                        : 15619157
File extension                   : thm
Format                           : JPEG
Format                           : JPEG
Format/Extensions usually used   : jpeg jpg jpe
Codec                            : JPEG
Codec                            : JPEG
Codec/Extensions usually used    : jpeg jpg jpe
File size                        : 10176
File size                        : 9.94 KiB
File size                        : 10 KiB
File size                        : 9.9 KiB
File size                        : 9.94 KiB
File size                        : 9.938 KiB

Image
Count                            : 50
Count of stream of this kind     : 1
Kind of stream                   : Image
Kind of stream                   : Image
Stream identifier                : 0
Format                           : JPEG
Codec                            : JPEG
Codec                            : JPEG
Width                            : 224
Width                            : 224 pixels
Height                           : 176
Height                           : 176 pixels
Resolution                       : 24
Resolution                       : 24 bits

--- end of mediainfo result ---

I've put the files on a ftp, you can download them at [http://habasnegras.free.fr/Fuze/](http://habasnegras.free.fr/Fuze/)

Many thanks again

Vincent

---

### Post by FakeOutdoorsman on 2009-05-30
Try these.  This command uses libxvid as the encoder:
```
ffmpeg -i input.avi -acodec libmp3lame -ar 44100 -ab 128k -ac 2 -vcodec libxvid -vtag DX50 -r 20 -b 512k -s 224x176 sansalibxvid.avi
```

This one uses FFmpeg's native *MPEG-4 part 2* encoder:
```
ffmpeg -i input.avi -acodec libmp3lame -ar 44100 -ab 128k -ac 2 -vcodec mpeg4 -vtag DX50 -r 20 -b 512k -s 224x176 sansalibxvid.avi
```
You may have to use the *-aspect 4:3* or *-aspect 16:9* options depending on the aspect ratio of your input video.

---

### Post by onekama_michigan on 2011-01-01
These related threads brought me to the video4fuze solution which allows video to be converted for Sansa Fuze on ubuntu

[http://forums.debian.net/viewtopic.php?p=286477](http://forums.debian.net/viewtopic.php?p=286477)
[http://ubuntuforums.org/showthread.php?t=827693&page=4](http://ubuntuforums.org/showthread.php?t=827693&page=4)
[http://code.google.com/p/video4fuze/](http://code.google.com/p/video4fuze/)

---

### Post by perspectoff on 2011-01-01
I have several Sansa Fuse players, which I generally use with Linux. I can put videos onto it directly from Linux.

Here are my instructions:

Ubuntuguide.org:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Sansa_Fuze](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Sansa_Fuze)

Kubuntuguide.org:
[http://kubuntuguide.org/Maverick#Sansa_Fuze](http://kubuntuguide.org/Maverick#Sansa_Fuze)

---

