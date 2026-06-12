---
title: "DVD playback problems"
date: 2010-05-31
forum: Multimedia Software
---

### Post by JRKF on 2010-05-31
Hi,

I recently got a Tarantino DVD collection and all the DVD's play fine except for Pulp Fiction. The problem is not with the disk because it plays on windows.

This is the kind of picture I get for the whole movie:

[IMG]http://www.eecs.qmul.ac.uk/%7Ejrkf/outgoing/playback.png[/IMG]


These are the error messages I get:
```

VLC media player 1.0.6 Goldeneye
[0x902c668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/joaofayad/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001ca
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000488
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00396880
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003968d7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003983f2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00398449
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00398b21
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00398b78
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
[0xb7000af8] main input error: ES_OUT_RESET_PCR called
[0xb7000af8] main input error: ES_OUT_RESET_PCR called
[0xb7027e98] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[0xb7014c68] pulse audio output: No. of Audio Channels: 6
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0xb7001df0] libmpeg2 decoder error: invalid picture encountered
[0xb7001df0] libmpeg2 decoder error: invalid picture encountered
[0xb7001df0] libmpeg2 decoder error: invalid picture encountered

```And it geeps sending the same "invalid picture encountered" error. Does anyone know a fix for this?

Thanks in advance.

---

### Post by xc3RnbFO8P on 2010-05-31
Read this:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8424980]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8424980")

---

### Post by JRKF on 2010-05-31
Solved! Thanks!

All I needed to do was to delete the folder corresponding to the movie I was trying to watch under ~/.dvdcss.

---

