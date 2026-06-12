---
title: "extract subtitles from mkv file."
date: 2013-09-17
forum: Multimedia Software
---

### Post by joshcanfield on 2013-09-17
ok so I am trying to put my mkv version of Death note on to a dvd to play in my xbox. I have tried to use devede to convert the mkv to iso and burn the iso with k3b. Here is the problem. when I do so I cant get the subtitles added to the video because they are contained in the mkv file. so I know there are ways of extracting the subtitles to certain files so I can re-add them with devede.

I tried to use mkvextract to get the sub titles but I keep running into this problem...idk if I am just over looking something or what...

canfield@canfield-laptop:~$ cd Downloads
canfield@canfield-laptop:~/Downloads$ mkvinfo Death-Note.mkv
+ EBML head
|+ Doc type: matroska
|+ Doc type version: 1
|+ Doc type read version: 1
+ Segment, size 1158601713
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4027)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v0.7.7 + libmatroska v0.8.1
| + Writing application: mkvmerge v2.2.0 ('Turn It On Again') built on Mar  4 2008 12:58:26
| + Duration: 7625.702s (02:07:05.702)
| + Date: Tue Feb 17 09:41:27 2009 UTC
| + Segment UID: 0x94 0xea 0x0a 0xde 0xcc 0x99 0xb8 0xc9 0x81 0xe1 0xfa 0xb8 0x14 0xcc 0x26 0x50
|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 2619835806
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
|  + CodecPrivate, length 40
|  + Default duration: 41.708ms (23.976 fps for a video track)
|  + Language: und
|  + Name: Encoded by ZangetsuZero ([http://www.demonoid.com](http://www.demonoid.com))
|  + Video track
|   + Pixel width: 720
|   + Pixel height: 400
|   + Interlaced: 0
|   + Display width: 720
|   + Display height: 400
| + A track
|  + Track number: 2
|  + Track UID: 2631325606
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: A_MPEG/L3
|  + Codec decode all: 1
|  + Default duration: 24.000ms (41.667 fps for a video track)
|  + Language: eng
|  + Audio track
|   + Sampling frequency: 48000
|   + Channels: 2
| + A track
|  + Track number: 3
|  + Track UID: 333448336
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: A_MPEG/L3
|  + Codec decode all: 1
|  + Default duration: 24.000ms (41.667 fps for a video track)
|  + Language: jpn
|  + Audio track
|   + Sampling frequency: 48000
|   + Channels: 2
| + A track
|  + Track number: 4
|  + Track UID: 940693895
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: S_VOBSUB
|  + Codec decode all: 1
|  + CodecPrivate, length 348
|  + Language: eng
|  + Content encodings
|   + Content encoding
|    + Order: 0
|    + Scope: 1 (1: all frames)
|    + Type: 0 (compression)
|    + Content compression
|     + Algorithm: 0 (ZLIB)
| + A track
|  + Track number: 5
|  + Track UID: 3985757593
|  + Track type: subtitles
|  + Enabled: 1
|  + Default flag: 0
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: S_VOBSUB
|  + Codec decode all: 1
|  + CodecPrivate, length 348
|  + Language: eng
|  + Content encodings
|   + Content encoding
|    + Order: 0
|    + Scope: 1 (1: all frames)
|    + Type: 0 (compression)
|    + Content compression
|     + Algorithm: 0 (ZLIB)
|+ EbmlVoid (size: 1024)
|+ Cluster
canfield@canfield-laptop:~/Downloads$ mkvextract tracks Death-Note.mkv 4:Death-Note.srt
Extracting track 4 with the CodecID 'S_VOBSUB' to the file 'Death-Note.srt'. Container format: VobSubs
Writing the VobSub index file 'Death-Note.idx'.
Progress: 100%
canfield@canfield-laptop:~/Downloads$ 

I get two files a .idx and a .sub file. 

DeVeDe wont accept the .idx or .sub file for me Is there another command I need to run to get a single subtitle file that is supported by devede.

---

### Post by ranger1021994 on 2013-09-18
You can try this :
[http://ubuntuforums.org/showthread.php?t=1805455&p=11055606#post11055606](http://ubuntuforums.org/showthread.php?t=1805455&p=11055606#post11055606)

---

