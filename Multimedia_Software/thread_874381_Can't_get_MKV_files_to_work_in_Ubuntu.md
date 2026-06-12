---
title: "Can't get MKV files to work in Ubuntu"
date: 2008-07-29
forum: Multimedia Software
---

### Post by holdie on 2008-07-29
So I've been trying to get my MKV files to work with either mplayer or VLC for quite some time now and thus far I've come up with nothing to show for it...

As far as I can tell, I've got all the codecs I need for mplayer (libmastroka, win32, etc)...and from what I understand VLC doesn't need anything extra in order to run MKV

Am I missing something here/doing something wrong?

Any help would be appreciated

---

### Post by shirilover on 2008-07-29
An .mkv is just a container for various audio/video streams.
So, what you need to know is what codecs are used for the streams contained within the mkv.
You can find this out by running from a terminal
```
 mkvinfo "your_file.mkv" 
```
or if you prefer a graphical interface you can run mkvinfo -g .

Also, keep in mind that the Xvideo renderer and a composited desktop(compiz) do not work well with each other. Try disabling compiz to see if playback improves.

---

### Post by holdie on 2008-07-30
alright, here's the output

also, I've got compiz disabled and am using the radeon envy driver
```
(MKVInfo) + EBML head at 0
(MKVInfo) |+ Doc type: matroska at 5
(MKVInfo) |+ Doc type version: 1 at 16
(MKVInfo) |+ Doc type read version: 1 at 20
(MKVInfo) + Segment, size 2348731116 at 24
(MKVInfo) |+ Seek head at 36
(MKVInfo) | + Seek entry at 41
(MKVInfo) |  + Seek ID: 0x15 0x49 0xa9 0x66  (KaxInfo) at 44
(MKVInfo) |  + Seek position: 4099 at 51
(MKVInfo) | + Seek entry at 56
(MKVInfo) |  + Seek ID: 0x16 0x54 0xae 0x6b  (KaxTracks) at 59
(MKVInfo) |  + Seek position: 4256 at 66
(MKVInfo) | + Seek entry at 71
(MKVInfo) |  + Seek ID: 0x11 0x4d 0x9b 0x74  (KaxSeekHead) at 74
(MKVInfo) |  + Seek position: 2348689344 at 81
(MKVInfo) | + Seek entry at 88
(MKVInfo) |  + Seek ID: 0x1c 0x53 0xbb 0x6b  (KaxCues) at 91
(MKVInfo) |  + Seek position: 2348667639 at 98
(MKVInfo) |+ EbmlVoid (size: 4027) at 105
(MKVInfo) |+ Segment information at 4135
(MKVInfo) | + Timecode scale: 1000000 at 4141
(MKVInfo) | + Muxing application: libebml v0.7.7 + libmatroska v0.8.1 at 4148
(MKVInfo) | + Writing application: mkvmerge v2.2.0 ('Turn It On Again') built on Mar  4 2008 12:58:26 at 4186
(MKVInfo) | + Duration: 4559.616s (01:15:59.616000000) at 4255
(MKVInfo) | + Date: Sat Jul  5 18:27:21 2008 UTC at 4262
(MKVInfo) | + Segment UID: 0xb4 0x8c 0xae 0xc4 0x53 0x71 0xf6 0x3f 0xb0 0x72 0xad 0xca 0x78 0xd5 0xed 0x56 at 4273
(MKVInfo) |+ Segment tracks at 4292
(MKVInfo) | + A track at 4298
(MKVInfo) |  + Track number: 1 at 4301
(MKVInfo) |  + Track UID: 1840095129 at 4304
(MKVInfo) |  + Track type: video at 4311
(MKVInfo) |  + Enabled: 1 at 4314
(MKVInfo) |  + Default flag: 1 at 4317
(MKVInfo) |  + Forced flag: 0 at 4320
(MKVInfo) |  + Lacing flag: 0 at 4324
(MKVInfo) |  + MinCache: 1 at 4327
(MKVInfo) |  + Timecode scale: 1.000000 at 4331
(MKVInfo) |  + Max BlockAddition ID: 0 at 4339
(MKVInfo) |  + Codec ID: V_MPEG4/ISO/AVC at 4343
(MKVInfo) |  + Codec decode all: 1 at 4360
(MKVInfo) |  + CodecPrivate, length 39 at 4363
(MKVInfo) |  + Default duration: 41.708ms (23.976 fps for a video track) at 4405
(MKVInfo) |  + Language: und at 4413
(MKVInfo) |  + Video track at 4420
(MKVInfo) |   + Pixel width: 1280 at 4422
(MKVInfo) |   + Pixel height: 720 at 4426
(MKVInfo) |   + Interlaced: 0 at 4430
(MKVInfo) |   + Display width: 1280 at 4433
(MKVInfo) |   + Display height: 720 at 4438
(MKVInfo) | + A track at 4443
(MKVInfo) |  + Track number: 2 at 4445
(MKVInfo) |  + Track UID: 2262003593 at 4448
(MKVInfo) |  + Track type: audio at 4455
(MKVInfo) |  + Enabled: 1 at 4458
(MKVInfo) |  + Default flag: 1 at 4461
(MKVInfo) |  + Forced flag: 0 at 4464
(MKVInfo) |  + Lacing flag: 1 at 4468
(MKVInfo) |  + MinCache: 0 at 4471
(MKVInfo) |  + Timecode scale: 1.000000 at 4475
(MKVInfo) |  + Max BlockAddition ID: 0 at 4483
(MKVInfo) |  + Codec ID: A_AC3 at 4487
(MKVInfo) |  + Codec decode all: 1 at 4494
(MKVInfo) |  + Default duration: 32.000ms (31.250 fps for a video track) at 4497
(MKVInfo) |  + Language: und at 4505
(MKVInfo) |  + Audio track at 4512
(MKVInfo) |   + Sampling frequency: 48000.000000 at 4514
(MKVInfo) |   + Channels: 6 at 4520
(MKVInfo) |+ EbmlVoid (size: 1024) at 4523
(MKVInfo) |+ Cluster at 5550
```

---

### Post by shirilover on 2008-07-30
OK, you have what I suppose is a high-definition movie in H.264/AC-3(5.1) at 720p.
Now, do you have enough processing power to play it?
HiDef H.264 video requires significant CPU speed to have smooth playback.
Also, what error does mplayer give you when you try to play the file?

---

