---
title: "problem with dvd playing"
date: 2006-10-08
forum: Multimedia &amp; Video
---

### Post by dphipps on 2006-10-08
I am tying to play a dvd on my laptop with libcssdvd but it is not working.  When I try to open it in Totem or Kaffiene they just close.  In Mplayer it opens for a second or so but shows no image.

The device manager shows my dvd drive as MATSHITADVD-ROM SR-8178.

If I run Totem form the camand line I get this output.

```
~$ totem
libdvdnav: Using dvdnav version 1.1.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/phipps/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000e3b0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000e633
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000e6b6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000e6cf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00010d44
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000335af
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000c150f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000da54e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0036987e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003c4c91
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003f49ec
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1608 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:667 ***
*** for pgc->program_map_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:668 ***
*** for pgc->cell_playback_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:669 ***
*** for pgc->cell_position_offset != 0 ***

libdvdnav: ifoRead_PGCIT failed
libdvdnav: *** pgci_ut handle is NULL ***
```

---

### Post by henriquemaia on 2006-10-08
Looks like from the error message that you're trying to play a wrong region DVD in your player. If you downloaded it, maybe you downloaded the wrong region one.

---

### Post by dphipps on 2006-10-09
I did not download it, and the dvd works on my desktop using the same programs.

---

### Post by dphipps on 2006-10-10
Any other idias.

If it is region problem (which I do not think it is) would that be in the hardware or software, and what could I do about it.

---

