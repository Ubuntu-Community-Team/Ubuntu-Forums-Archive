---
title: "Totem keeps crashing"
date: 2010-02-07
forum: Multimedia Software
---

### Post by 311005901 on 2010-02-07
Totem keeps crashing when I try to play an encrypted DVD. ```
tim@iMac-Ubuntu:~$ totem
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: E2938
libdvdnav: DVD Serial Number: 36365822
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/tim/.dvdnav/E2938.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000135
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000716f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00007173
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00007189
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0000fd3f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0001eed0
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
totem: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted

```
I've got libdvdread3 installed. What can I do?

---

### Post by 311005901 on 2010-02-07
Meh. Restarted and it took care of itself.

---

