---
title: "Playing video problems - lost of sound"
date: 2022-08-20
forum: Multimedia Software
---

### Post by py-ohayo on 2022-08-20
Hello,
I encountered problems when playing some videos: jumping with the slider to another position causes sound to drop out, i.e. the video plays without sound.
After exploring the properties of these files with ffmpeg, I discovered that one of the parameters had a rather strange value: **[FONT=courier new]codec_time_base=10383984/519199199[/FONT]**.
Probably this is the cause of problem ?
If yes, how ti fix it ?
Sincerely

---

### Post by Yellow Pasque on 2022-08-20
What program are you using to play the video? Have you tried starting the program from the terminal to see if there are any error messages (or looking at logs if using something like VLC or mpv)?
> I discovered that one of the parameters had a rather strange value: codec_time_base=10383984/519199199
Why do you think it is a problem? And if it is the problem, then you may have poorly encoded video files and you should run 'mediainfo' on those files to examine the details.

---

### Post by py-ohayo on 2022-08-21
Tried with different players: 

[LIST]
[*]VLC and "Videos" (Ubuntu)
[*]VLC, "Films & TV" and "Windows Media Player" (Windows 10)
[/LIST]
The effect is the same in all cases - once cursor is advanced, video is played without sound.
[COLOR=#0000cd][I]
Why do you think it is a problem? And if it is the problem, then you may  have poorly encoded video files and you should run 'mediainfo' on those  files to examine the details. 		[/I][/COLOR]

It's just a guess.
I compared these videos with others, where there are no such problems.
In "good" videos this parameter is **1/50**.
I didn't encoded these videos - I downloaded them from TV website ([https://revoir.tv5monde.com/](https://revoir.tv5monde.com/)).

Here is mediainfo data:

General
Complete name                            : filename.mp4
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom (isom/iso2/avc1/mp41)
File size                                : 1.42 GiB
Duration                                 : 1 h 36 min
Overall bit rate mode                    : Variable
Overall bit rate                         : 2 111 kb/s
Writing application                      : Lavf57.83.100

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Main@L4
Format settings                          : CABAC / 2 Ref Frames
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 2 frames
Format settings, GOP                     : M=3, N=90
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 1 h 36 min
Bit rate mode                            : Constant
Bit rate                                 : 2 100 kb/s
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Variable
Frame rate                               : 25.000 FPS
Minimum frame rate                       : 12.500 FPS
Maximum frame rate                       : 90 000.000 FPS
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.041
Stream size                              : 1.41 GiB (99%)

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : mp4a-40-2
Duration                                 : 2 min 39 s
Bit rate mode                            : Variable
Bit rate                                 : 253 kb/s
Maximum bit rate                         : 256 kb/s
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 kHz
Frame rate                               : 46.875 FPS (1024 SPF)
Compression mode                         : Lossy
Stream size                              : 4.81 MiB (0%)
Default                                  : Yes
Alternate group                          : 1

---

### Post by py-ohayo on 2022-08-21
Well, with **mediainfo** I see that audio stream isn't properly downloaded.
Thanks !

---

