---
title: "MKV to DVD"
date: 2010-01-12
forum: Multimedia Software
---

### Post by paul.maddox on 2010-01-12
Hi,

I have a MKV video file that I want to write to DVD so that I can give it to a non-techy neighbour!

Can anyone point me in the right direction on how to do this? Ideally from the command line if possible.

Thanks.

ps. I've attached the mkvinfo of the file in case it makes any difference.

```

+ EBML head
|+ Doc type: matroska
|+ Doc type version: 2
|+ Doc type read version: 2
+ Segment, size 1173349293
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4044)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v0.7.7 + libmatroska v0.8.1
| + Writing application: mkvmerge v2.9.7 ('Tenderness') built on Jul  1 2009 18:43:35
| + Duration: 2919.040s (00:48:39.040)
| + Date: Thu Nov  5 02:19:42 2009 UTC
| + Segment UID: 0xb4 0x58 0x97 0x8c 0x20 0x45 0x73 0xf4 0x88 0xae 0x3e 0x0f 0x01 0xe5 0x57 0x4d
|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 3215259524
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
|  + CodecPrivate, length 42
|  + Default duration: 40.000ms (25.000 fps for a video track)
|  + Language: und
|  + Video track
|   + Pixel width: 1280
|   + Pixel height: 720
|   + Interlaced: 0
|   + Display width: 1280
|   + Display height: 720
| + A track
|  + Track number: 2
|  + Track UID: 3904706192
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: A_AC3
|  + Codec decode all: 1
|  + Default duration: 32.000ms (31.250 fps for a video track)
|  + Language: und
|  + Audio track
|   + Sampling frequency: 48000
|   + Channels: 6
|+ EbmlVoid (size: 1024)
|+ Cluster

```

---

### Post by ugutugut on 2010-01-22
Try Devede, it is in the repository

---

### Post by inman2787 on 2010-10-06
[ConvertXtoDVD]("http://www.****************/wiki/VSO_ConvertXtoDVD_-_AVI_to_DVD_Video_Converter") usually encodes fast but I never fukked with it.And it support burn MKV files to DVD fast,but included a loss of quality.

---

### Post by SeijiSensei on 2010-10-06
You can use mencoder and dvdauthor to do this, but it's a bit of a pain.  See [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html) for details.

---

