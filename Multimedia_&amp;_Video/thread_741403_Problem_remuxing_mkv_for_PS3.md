---
title: "Problem remuxing mkv for PS3"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by alexanderdavidsen on 2008-03-31
I have a mkv file with a DTS soundtrack that I need to demux to mp4 to be able to use it on my ps3. 

This is what I do: 
Extract the video and audio track 
```
mkvextract tracks file.mkv 1:video.h264 2:audio.ac3 

```

Change a bit in the video-file 
```
perl -pi.bak -e 's{\x67\x64\x00\x33}{\x67\x64\x00\x29}' video.h264 

```

make a fifo 
```
mkfifo audiodump.wav 

```

reencode so the audio will be playable on my PS3 
```
neroAacEnc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -channels 6 -ao pcm:fast 
```


When I run this last command i get the following errors: 
```


************************************************************* 
*                                                           * 
*  Nero Digital Audio Reference MPEG-4 & 3GPP Audio Encoder * 
*  Copyright 2007 Nero AG                                   * 
*  All Rights Reserved Worldwide                            * 
*                                                           * 
*  Package build date: Aug  6 2007                          * 
*                                                           * 
*                                                           * 
*  See -help for a complete list of available parameters.   * 
*                                                           * 
************************************************************* 

MPlayer 2:1.0~rc1-0ubuntu9.3 (C) 2000-2006 MPlayer Team 
CPU: AMD Athlon(TM) XP 2200+ (Family: 6, Model: 8, Stepping: 1) 
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0 
Compiled with runtime CPU detection. 
Can't open joystick device /dev/input/js0: No such file or directory 
Can't init input joystick 
mplayer: could not connect to socket 
mplayer: No such file or directory 
Failed to open LIRC support. You will not be able to use your remote control. 

Playing audio.ac3. 
libavformat file format detected. 
========================================================================== 
Forced audio codec: mad 
Opening audio decoder: [liba52] AC3 decoding with liba52 
Using SSE optimized IMDCT transform 
a52: CRC check failed!  
Unimplemented resampler for mode 0x7 -> 6 channels conversion - Contact MPlayer developers! 
Using MMX optimized resampler 
AUDIO: 32000 Hz, 5 ch, s16le, 56.0 kbit/2.19% (ratio: 7000->320000) 
Selected audio codec: [a52] afm: liba52 (AC3-liba52) 
========================================================================== 
[AO PCM] File: audiodump.wav (WAVE) 
PCM: Samplerate: 32000Hz Channels: Stereo Format s16le 
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast 
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default). 
AO: [pcm] 32000Hz 5ch s16le (2 bytes per sample) 
Video: no video 
Starting playback... 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
a52: CRC check failed!  0 (27:15.9) ??,?% 
a52: error at resampling 
A:   0.9 (00.9) of 1636.0 (27:15.9) ??,?% 
ERROR: Could not initialize SBR 
```


Any ideas why this errors are occuring? I get picture but no audio when i merge the video and audio files together later on with mp4box...

---

### Post by Onay on 2008-04-01
Yeah that is unusual... I've never seen that perl command, but I'm assuming you're just changing that "33" value to "29" in the hex code. Can you give us the mkvinfo of the file (to check to see what codec the audio is)? Have you tried using any other mkv's ?

and how big is the file?

---

### Post by alexanderdavidsen on 2008-04-01
I have this problem on every file with DTS soundtrack. I have tried with a lot of mkv-files. This particular mkv-file is just a sample, so its 50mb. But I have the same problem on 2gb, 4gb, 6gb and 8gb files.

This is the mkvinfo for the file:
```
+ EBML head
|+ Doc type: matroska
|+ Doc type version: 1
|+ Doc type read version: 1
+ Segment, size 45852857
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4012)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v0.7.7 + libmatroska v0.8.1
| + Writing application: mkvmerge v2.1.0 ('Another Place To Fall') built on Aug 19 2007 13:40:07
| + Duration: 60.610s (00:01:00.610000000)
| + Date: Tue Mar  4 23:30:21 2008 UTC
| + Title: No Country for Old Men (2007)
| + Segment UID: 0x91 0xa2 0xe8 0x85 0x44 0x6e 0xc8 0x2b 0x81 0x67 0x4a 0x7a 0x3b 0x1b 0xf7 0x7e
|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 1
|  + Track type: video
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 1
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: V_MPEG4/ISO/AVC
|  + Codec decode all: 1
|  + CodecPrivate, length 167
|  + Default duration: 41.708ms (23.976 fps for a video track)
|  + Language: eng
|  + Video track
|   + Pixel width: 1280
|   + Pixel height: 544
|   + Interlaced: 0
|   + Display width: 40
|   + Display height: 17
| + A track
|  + Track number: 2
|  + Track UID: 4033331100
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: A_DTS
|  + Codec decode all: 1
|  + Language: eng
|  + Audio track
|   + Sampling frequency: 48000.000000
|   + Channels: 6
| + A track
|  + Track number: 3
|  + Track UID: 1503251096
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/***
|  + Codec decode all: 1
|  + CodecPrivate, length 795
|  + Language: eng
| + A track
|  + Track number: 4
|  + Track UID: 2663580328
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/***
|  + Codec decode all: 1
|  + CodecPrivate, length 793
|  + Language: fin
| + A track
|  + Track number: 5
|  + Track UID: 4056360347
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/***
|  + Codec decode all: 1
|  + CodecPrivate, length 793
|  + Language: swe
| + A track
|  + Track number: 6
|  + Track UID: 992888222
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/***
|  + Codec decode all: 1
|  + CodecPrivate, length 793
|  + Language: cze
| + A track
|  + Track number: 7
|  + Track UID: 1415232687
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/***
|  + Codec decode all: 1
|  + CodecPrivate, length 793
|  + Language: fre
| + A track
|  + Track number: 8
|  + Track UID: 4011405230
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/***
|  + Codec decode all: 1
|  + CodecPrivate, length 793
|  + Language: hun
| + A track
|  + Track number: 9
|  + Track UID: 3528041638
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/***
|  + Codec decode all: 1
|  + CodecPrivate, length 793
|  + Language: rum
| + A track
|  + Track number: 10
|  + Track UID: 3982123928
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/***
|  + Codec decode all: 1
|  + CodecPrivate, length 793
|  + Language: slv
| + A track
|  + Track number: 11
|  + Track UID: 1197950360
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/***
|  + Codec decode all: 1
|  + CodecPrivate, length 793
|  + Language: spa
|+ EbmlVoid (size: 1024)
|+ Attachments
| + Attached
|  + File name: CronosPro-Bold.ttf
|  + Mime type: application/x-truetype-font
|  + File data, size: 108928
|  + File UID: 3565965979
| + Attached
|  + File name: CronosPro-Semibold.ttf
|  + Mime type: application/x-truetype-font
|  + File data, size: 109724
|  + File UID: 4207133616
| + Attached
|  + File name: CronosPro-SemiboldIt.ttf
|  + Mime type: application/x-truetype-font
|  + File data, size: 135684
|  + File UID: 3332045237
|+ Cluster

```

What I think I need to do is recode the dts-file to ac3 as these files has dts-soundtracks. How can I do this?

---

### Post by Onay on 2008-04-01
Well I'm not expert on these different formats and containers, but I see in your Nero encoding command you're using the extracted audio.ac3 file to convert. Why not try to extract the track as a .dts file, then use that file with the encoder and see if that works

---

