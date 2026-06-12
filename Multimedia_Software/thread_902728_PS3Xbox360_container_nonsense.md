---
title: "PS3/Xbox360 container nonsense"
date: 2008-08-27
forum: Multimedia Software
---

### Post by pormogo on 2008-08-27
So I recently have wanted to play some high definition video files via my PS3. Unfortunately it seems like .mkv has quickly become the container standard for HD video on the net. No big deal, recontainerizing the media shouldn't be that big of a problem. Upon searching the forums and google I found a plethora of different scripts, methods, and applications used for doing these video conversions. However most of them involved re encoding the av streams inside the container. This doesn't make much sense to me. What's the point in having a nice big HD file if you're going to re encode it and loose quality in the process? 

As an example I took one file and ran mkvinfo on it to check the a/v codec IDs (bolded). 

[i]+ EBML head
|+ Doc type: matroska
|+ Doc type version: 1
|+ Doc type read version: 1
+ Segment, size 4685744437
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4010)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v0.7.6 + libmatroska v0.8.0
| + Writing application: mkvmerge v1.6.5 ('Watcher Of The Skies') built on Dec  7 2005 18:53:53
| + Duration: 6905.352s (01:55:05.352000000)
| + Date: Wed Jul 26 21:02:23 2006 UTC
| + Title: 
| + Segment UID: 0x88 0x29 0x75 0xbf 0x00 0xae 0xaf 0x3a 0x9e 0xca 0xab 0xfb 0x76 0xa4 0xa9 0x7f
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
|  **+ Codec ID: V_MPEG4/ISO/AVC**
|  + Codec decode all: 1
|  + CodecPrivate, length 130
|  + Default duration: 41.708ms (23.976 fps for a video track)
|  + Language: eng
|  + Name: 
|  + Video track
|   + Pixel width: 1280
|   + Pixel height: 544
|   + Interlaced: 0
|   + Display width: 40
|   + Display height: 17
| + A track
|  + Track number: 2
|  + Track UID: 1891935385
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  **+ Codec ID: A_AC3**
|  + Codec decode all: 1
|  + Default duration: 32.000ms (31.250 fps for a video track)
|  + Language: eng
|  + Name: AC3 2.0
|  + Audio track
|   + Sampling frequency: 48000.000000
|   + Channels: 2
| + A track
|  + Track number: 3
|  + Track UID: 641360517
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
|  + CodecPrivate, length 879
|  + Language: eng
|  + Name: English ***
|+ EbmlVoid (size: 1024)
|+ Attachments
| + Attached
|  + File name: TCCEB.TTF
|  + Mime type: application/x-truetype-font
|  + File data, size: 74708
|  + File UID: 2479244476
| + Attached
|  + File name: TCCEB.TTF
|  + Mime type: application/x-truetype-font
|  + File data, size: 74708
|  + File UID: 65136813
|+ Cluster
[/i]

According to that the av codecs are supported by my PS3, the only issue here is that the container format is not. So following this logic I should be able to use ffmpeg and copy both of those streams into a new mp4 container correct? I tried using the following command

*$ffmpeg -i input_file.mkv -vcodec copy -acodec copy -f mp4 ./output.mp4*

Which seems like it should function correct? copy both of the compatible streams and pack them in an mp4. Maybe I'm making some kind of judgement error because the following keeps happening. 

[i]FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:28:49, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[matroska @ 0x7f2599f52160]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0x7f2599f52160]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0x7f2599f52160]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0x7f2599f52160]Ignoring seekhead entry for ID=0x1941a469
[matroska @ 0x7f2599f52160]Unknown entry 0x73a4 in info header
[matroska @ 0x7f2599f52160]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0xaa - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0xaa - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7f2599f52160]Unknown track header entry 0xaa - ignoring
[matroska @ 0x7f2599f52160]Unknown matroska file header ID 0x1941a469
Input #0, matroska, from 'input.mkv':
  Duration: 01:55:05.3, bitrate: N/A
  Stream #0.0: Video: h264, yuv420p, 1280x544, 23.98 fps(r)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo
Output #0, mp4, to './output.mp4':
  Stream #0.0: Video: h264, yuv420p, 1280x544, q=2-31, 1000.00 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mp4 @ 0x7f2599f52160]track 1: codec frame size is not set
Could not write header for output file #0 (incorrect codec parameters ?)
[/i]

Am I doing something wrong? Do I have a fundamental misunderstanding of something here? Is it necessary to re encode video and audio when simply changing containers?

---

### Post by Loacoon on 2008-10-01
I'm having the exact same problem. I searched on the need, and it looks like nobody nevers aswers to this kind of questions.
It's like even FFMPEG devs doesn't know the answer... :/

Any idea?

---

