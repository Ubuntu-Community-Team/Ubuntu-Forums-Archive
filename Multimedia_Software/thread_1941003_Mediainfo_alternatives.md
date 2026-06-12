---
title: "Mediainfo alternatives ?"
date: 2012-03-14
forum: Multimedia Software
---

### Post by LiNIX420 on 2012-03-14
Hi!
Didnt find a Welcome forum, so just wanted to say hi to the community & linux users.
I just wanted to try Ubuntu cause have heard it was a nice clean OS.
Tryed it and not going back to Windows.
Thanks for the OS who ever made it ;)

Anyways, my question is are there any alternatives to sofware **'' mediainfo ''**
I want to get mediainfo from .mkv files like:
Video/audio bitrate, size, resolution is the most important.

Big thanks!

---

### Post by papibe on 2012-03-14
Hi LiNIX420. Welcome to the forums!

The actual mediainfo application is available via a ppa (Personal Package Archive).

First, you need to add the repository. Open a terminal and run:
```
sudo add-apt-repository ppa:shiki/mediainfo
```
Then you update the software sources:
```
sudo apt-get update
```
Then, you are almost set. There are two versions: a command line tools called 'mediainfo', or a graphical version called 'mediainfo-gui'.

At this point you have a couple of options: opening the Software Center and install it from there, or going again into the terminal and do:
```
sudo apt-get install mediainfo-gui
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by LiNIX420 on 2012-03-14
Yes yes.
Wow it was easy ti install.
Works perfectly!
Thanks!

---

### Post by papibe on 2012-03-14
:D Great! Mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.
Regards.

---

### Post by LiNIX420 on 2012-03-14
Hehe, did it manually is it ok? Its night and im tired dont have energy to search...
EDIT: Hehe u linked it, DONE!
Thanks again!

---

### Post by andrew.46 on 2012-03-15
If you are after an alternative to mediainfo for mkv files specifically there is always *mkvinf*o:

```

andrew@skamandros~/media/testing$**[COLOR="Red"] mkvinfo Star.Wars.Trailer.mkv [/COLOR]**
+ EBML head
|+ EBML version: 1
|+ EBML read version: 1
|+ EBML maximum ID length: 4
|+ EBML maximum size length: 8
|+ Doc type: matroska
|+ Doc type version: 2
|+ Doc type read version: 2
+ Segment, size 72375149
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4044)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v1.2.2 + libmatroska v1.3.0
| + Writing application: mkvmerge v5.4.0 ('Piper') built on Mar 11 2012 08:06:36
| + Duration: 88.448s (00:01:28.448)
| + Date: Thu Mar 15 11:51:52 2012 UTC
| + Segment UID: 0x89 0xa8 0x92 0x14 0x94 0x3a 0x81 0xf1 0x5a 0x32 0x67 0x13 0xb9 0x88 0xd6 0x60 
|+ Segment tracks
| + A track
|  + Track number: 1 (track ID for mkvmerge & mkvextract: 0)
|  + Track UID: 2667570447
|  + Track type: video
|  + Lacing flag: 0
|  + MinCache: 1
|  + Codec ID: V_MPEG4/ISO/AVC
|  + CodecPrivate, length 49 (h.264 profile: High @L4.0)
|  + Default duration: 41.711ms (23.974 frames/fields per second for a video track)
|  + Language: und
|  + Video track
|   + Pixel width: 1920
|   + Pixel height: 816
|   + Display width: 1920
|   + Display height: 817
|  + Content encodings
|   + Content encoding
|    + Content compression
|     + Algorithm: 3 (header removal)
|     + Settings: length 1, data: 0x00
| + A track
|  + Track number: 2 (track ID for mkvmerge & mkvextract: 1)
|  + Track UID: 4014176587
|  + Track type: audio
|  + Codec ID: A_AAC
|  + CodecPrivate, length 2
|  + Default duration: 21.333ms (46.875 frames/fields per second for a video track)
|  + Audio track
|   + Sampling frequency: 48000
|   + Channels: 2
|+ EbmlVoid (size: 1103)
|+ Cluster
andrew@skamandros~/media/testing$ 

```

---

