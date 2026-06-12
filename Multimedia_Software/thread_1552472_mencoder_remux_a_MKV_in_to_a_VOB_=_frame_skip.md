---
title: "mencoder remux a MKV in to a VOB = frame skip?"
date: 2010-08-13
forum: Multimedia Software
---

### Post by Ferrat on 2010-08-13
As the topic says I'm trying to remux a MKV file in to a VOB just to switch the container using mencoder but I'm having a problem, it seems the fps won't stay the same. 

using just -ovc copy and -oac copy I get lots and lots of frame skips, the mkv file identifies itself as 23.976 fps and it is but even if I use -ofps 23.976 or 24000/1001 I still get frame skips, if I try -ofps 25 I get duplicates, it seems the fps is somewhere around 24.4 - 24.5 fps but there isn't a good number because even somewhere in the middle of that I get both skips and dups, it almost seems as if it got a variable frame rate? 

Anyone got any suggestion what the problem could be? all I wanna do is a simple remux from mkv to vob, no re-encoding, I could also try a remux to mp4 if someone got that down :P 

mkvinfo
```
+ EBML head
|+ Doc type: matroska
|+ Doc type version: 1
|+ Doc type read version: 1
+ Segment, size 4671648637
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4025)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v0.7.7 + libmatroska v0.8.1
| + Writing application: mkvmerge v2.2.0 ('Turn It On Again') built on Mar  4 2008 13:20:25
| + Duration: 5355.360s (01:29:15.360)
| + Date: Sat Jul  3 01:07:26 2010 UTC
| + Segment UID: 0x9e 0x5b 0x95 0xfb 0xac 0x7d 0xbd 0x54 0x96 0x7e 0x94 0xf1 0x45 0x22 0x89 0x92
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
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: V_MPEG4/ISO/AVC
|  + Codec decode all: 1
|  + CodecPrivate, length 41
|  + Default duration: 41.708ms (23.976 fps for a video track)
|  + Language: eng
|  + Video track
|   + Pixel width: 1280
|   + Pixel height: 692
|   + Interlaced: 0
|   + Display width: 320
|   + Display height: 173
| + A track
|  + Track number: 2
|  + Track UID: 2420895660
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: A_DTS
|  + Codec decode all: 1
|  + Language: eng
|  + Name: &#33521;&#35821;
|  + Audio track
|   + Sampling frequency: 48000
|   + Channels: 6
|+ EbmlVoid (size: 1024)
|+ Cluster

```

Mencoder output 
```
MEncoder SVN-r31226-4.4.3 (C) 2000-2010 MPlayer Team

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0x1673b3a1
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_DTS) "&#33521;&#35821;", -aid 0, -alang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x692  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:31  fourcc:0x31637661  size:1280x692  fps:23.976  ftime:=0.0417
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
videocodec: framecopy (1280x692 24bpp fourcc=31637661)
audiocodec: framecopy (format=2001 chans=2 rate=48000 bits=16 B/s=192000 sample-1)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   1.6s     38f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.083 [2569:1536]
Skipping frame!

```

also using -of lavf or mpeg doesn't work, lavf can't handle the picture because it's too big and mpeg just crashes at header creation

---

### Post by FakeOutdoorsman on 2010-08-14
Did you try FFmpeg?
```
ffmpeg -i input.foo -vcodec copy -acodec copy output.vob
```
Although it appears your video input is not MPEG-2 Part 2 or MPEG-1 Part 2 which is what you usually find in a vob.

---

