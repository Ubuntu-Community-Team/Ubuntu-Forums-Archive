---
title: "Can't play DVDs after installing codecs and libraries"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by Leon945 on 2007-08-25
Hi All!
I'n having trouble playing DVDs...
The DVD im trying to play is Matrix Revolutions (if it helps at all)}
and this is the error i get from MPlayer

i don't really know whats going on..

```
Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
There are 10 titles on this DVD.
There are 33 chapters in this DVD title.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0001e406
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00062f92
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00342c65
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: fr aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: fr
subtitle ( sid ): 2 language: es
number of subtitles on disk: 3
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  7500.0 kbps (937.5 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.

```

any help?

---

### Post by uclalinux on 2007-08-25
aptitude install libdvdcss2 libdvdread3 libdvdnav4 vlc

---

### Post by Leon945 on 2007-08-25
Thanks!

i didn't know i had to use VLC...
it works with VLC 
thanks again

---

