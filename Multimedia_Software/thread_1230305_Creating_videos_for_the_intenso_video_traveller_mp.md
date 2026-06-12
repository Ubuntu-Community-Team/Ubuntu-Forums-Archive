---
title: "Creating videos for the intenso video traveller mp3 player"
date: 2009-08-03
forum: Multimedia Software
---

### Post by hoover67 on 2009-08-03
Hi folks,

my daughter bought the abovementioned mp3 player today because on the box it said "Linux", which she liked :D

Everything works ok so far, however I'd like to convert flv videos for the device using ffmpeg instead of the windows only "converter tool" that comes with the player.

According to "file", both files are identical (the "_linux" one was created using ffmpeg, the other using the converter tool): 

```
$ file nidan_neu.avi
nidan_neu.avi: RIFF (little-endian) data, AVI, 128 x 128, ~15 fps,
video: XviD, audio: MPEG-1 Layer 1 or 2 (stereo, 44100 Hz)



$ file nidan_linux.avi
nidan_linux.avi: RIFF (little-endian) data, AVI, 128 x 128, ~15 fps,
video: XviD, audio: MPEG-1 Layer 1 or 2 (stereo, 44100 Hz)
```

Here are the ffmpeg params that were used for the conversion: 

```
ffmpeg -i nidan.flv -vcodec divx -s 128x128 -ar 44100 -r 15 nidan.avi
```

Any ideas why the player still refuses the linux version, but plays the converter tool one fine? Any ideas how to extract more info on the files short of using a hex editor? 

TIA for your help,

Uwe

---

### Post by FakeOutdoorsman on 2009-08-03
You're on the right track and media players can be tricky.  Use [mediainfo](https://launchpad.net/~shiki/+archive/mediainfo) to see some more details and post them here:
```
mediainfo nidan_neu.avi
```

---

### Post by hoover67 on 2009-08-04
Thanks for your help, folks. Meanwhile I've "reverse engineered" the converter that comes with the device and found it's only a gui wrapper around mencoder for win32 8-P 

I found some options that create working videos for the intenso video traveller, though with heavy sound lag so I guess I need to do more experimenting. 

Here's the mencoder parameters I tried: 

```
mencoder -ofps 15 -vf-add scale=128:128 -vf-add expand=128:128:-1:-1:1
-srate 4100   -ovc xvid -xvidencopts bitrate=400:max_bframes=0:quant_type=h263:me_quality=0  -oac lavc
-lavcopts acodec=mp2:abitrate=96 Desktop/sandan.avi -o sandan.avi
```

All the best & thanks again for your help,

Uwe

---

### Post by adater on 2010-06-28
This are the results of mediainfo for the original video: 
> 
MediaInfo:
General
Complete name                    : /home/username/Desktop/inputVideo.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 759 KiB
Duration                         : 111ms
Overall bit rate                 : 56.0 Mbps
Writing application              : MEncoder Sherpya-MinGW-20060312-4.1.0
Writing library                  : MPlayer

Video
ID                               : 0
Format                           : MPEG-4 Visual
Codec ID                         : XVID
Codec ID/Hint                    : XviD
Duration                         : 111ms
Width                            : 176 pixels
Height                           : 220 pixels
Display aspect ratio             : 0.800
Frame rate                       : 18.000 fps

Audio
ID                               : 1
Format                           : MPEG Audio
Format version                   : Version 1
Codec ID                         : 50
Duration                         : 110ms
Bit rate                         : 64.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Stream size                      : 880 Bytes (0%)
Alignment                        : Split accross interleaves


This are the results of mediainfo for the resulting video using: ffmpeg -i inputVideo.xyz -s 176x220 -aspect 4:5 -vcodec mpeg4 -r 18 -b 9911k -ar 44100 -ab 64k -acodec mp2 -ac 2 outputVideo.avi

> 
General
Complete name                    : /home/username/Desktop/inputVideo.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 36.9 MiB
Duration                         : 3mn 30s
Overall bit rate                 : 1 471 Kbps
Writing application              : Lavf52.31.0

Video
ID                               : 0
Format                           : MPEG-4 Visual
Codec ID                         : FMP4
Duration                         : 3mn 30s
Bit rate                         : 1 396 Kbps
Width                            : 176 pixels
Height                           : 220 pixels
Display aspect ratio             : 0.800
Frame rate                       : 18.000 fps
Bits/(Pixel*Frame)               : 2.003
Stream size                      : 35.0 MiB (95%)

Audio
ID                               : 1
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 2
Codec ID                         : 50
Duration                         : 3mn 30s
Bit rate mode                    : Constant
Bit rate                         : 64.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Stream size                      : 1.61 MiB (4%)
Alignment                        : Aligned on interleaves
Interleave, duration             : 26 ms (0.47 video frame)
Interleave, preload duration     : 235 ms


This are the results of mediainfo for the resulting video using: mencoder -ofps 18 -vf-add scale=176:220 -vf-add expand=176:220:-1:-1:1 -srate 44100 -ovc xvid -xvidencopts bitrate=400:max_bframes=0:quant_type=h263:me_quality=0  -oac lavc -lavcopts acodec=mp2:abitrate=64 Shakira\ -\ \ Waka\ Waka\ -\ Official\ 2010\ FIFA\ World\ Cup.mkv -o wakaMem.avi
> 
General
Complete name                    : /home/username/Desktop/inputvideo.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 11.9 MiB
Duration                         : 3mn 30s
Overall bit rate                 : 472 Kbps
Writing application              : MEncoder SVN-r1.0~rc3+svn20090426-4.4.3
Writing library                  : MPlayer

Video
ID                               : 0
Format                           : MPEG-4 Visual
Codec ID                         : XVID
Codec ID/Hint                    : XviD
Duration                         : 3mn 30s
Bit rate                         : 397 Kbps
Width                            : 176 pixels
Height                           : 220 pixels
Display aspect ratio             : 0.800
Frame rate                       : 18.000 fps
Bits/(Pixel*Frame)               : 0.570
Stream size                      : 9.97 MiB (84%)

Audio
ID                               : 1
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 2
Codec ID                         : 50
Duration                         : 3mn 30s
Bit rate mode                    : Constant
Bit rate                         : 64.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Stream size                      : 1.61 MiB (14%)
Alignment                        : Aligned on interleaves
Interleave, duration             : 26 ms (0.47 video frame)
Interleave, preload duration     : 522 ms


---

