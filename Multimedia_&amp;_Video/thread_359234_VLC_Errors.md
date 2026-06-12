---
title: "VLC Errors"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by sudarshantk on 2007-02-11
Hi,
I got the following error message while starting VLC player to play DVDs.
------------------------------------------------------------------------------------------------------
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: THE_MATRIX_16X9LB_N_AMERICA
libdvdnav: DVD Serial Number: 27028BAA
libdvdnav: DVD Title (Alternative): THE_MATRIX_16X9LB_N_AMERICA
libdvdnav: Unable to find map file '/home/su817200/.dvdnav/THE_MATRIX_16X9LB_N_AMERICA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdread: Can't seek to block 540405
libdvdread: Invalid IFO for title 2 (VTS_02_0.IFO).
libdvdnav: ifoOpenVTSI failed - CRASHING!!!
vlc: vm.c:199: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)
--------------------------------------------------------------------------------------------------
Am I missing any package. Please let me know.

Rgds,
Sudarshantk

---

### Post by Jovec on 2007-02-11
> **sudarshantk said:**
> 
libdvdread: Encrypted DVD support unavailable.

Would be my guess.  Try following the instructions [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/dvdplayback.html").

---

