---
title: "DVD: Error reading NAV packet. 9.10"
date: 2010-03-01
forum: Multimedia Software
---

### Post by asdsamppa on 2010-03-01
Hi,
I've been using ubuntu now for over 2 years but i can't figure this DVD error out. I have installed *libdvdnav4, libdvdread4* and done this: ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```This is what I got in terminal while running DVD with gxine:
```
libdvdnav: Using dvdnav version 1.1.16.3 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: *****
libdvdnav: DVD Serial Number: 2D1C6F3A
libdvdnav: DVD Title (Alternative): *****
libdvdnav: Unable to find map file '/home/samu/.dvdnav/*****.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000561f0
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x000561f0)
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00056422
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00056422)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000bf227
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000cce28
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x000cce28)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0036477a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x0036477a)!!
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 3
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
xine-lib: error: Read error from:: Error reading NAV packet.

```I've been trying to search and solve this problem by my own but I can't.
Ps. this is my first post and I'm from Finland so don't bay me or my english::smoke

---

