---
title: "lsdvd unable to read IFO"
date: 2009-11-05
forum: Multimedia Software
---

### Post by supwesyde on 2009-11-05
I'm running Karmic and up until recently I've able to rip dvd's using acidrip.  I'm not sure what happened, but after adding the medibuntu repo I no longer can.  DVD playback is still fine, but acidrip complains

> Can't read DVD track.  Faulty Disc?I think this is due to a problem with lsdvd.  When I run lsdvd in a terminal I get the following 

> libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Unable to read VTS_TMAP_ENT.
*** Zero check failed in ifo_read.c:1567
    for c_adt->zero_1 = 0xd209

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Can't allocate memory for file read!

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Invalid title IFO (VTS_01_0.IFO).
Can't open ifo 1!I've tried reinstalling lsdvd, libdvdread4, libdvdnav4, libdvdcss2 and the gstreamer plugins but no luck.

---

