---
title: "VLC segfault when attempting to play DVDs"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by meldroc on 2007-01-01
When I attempt to play a DVD using VLC, the program instantly segfaults.  I have libdvdcss installed, and in fact, I can play a DVD using Kaffeine.  If it makes a difference, I'm doing this on an x86-64 Kubuntu installation.

Anyone else experiencing these crashes?

If I run VLC from a shell, I get the following output in a shell when I run VLC, and attempt to open a DVD.
```

meldroc@meldroc-laptop:~$ vlc
VLC media player 0.8.6 Janus
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: STARTRK2
libdvdnav: DVD Serial Number: 28A55E1C
libdvdnav: DVD Title (Alternative): STARTRK2
libdvdnav: Unable to find map file '/home/meldroc/.dvdnav/STARTRK2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000126
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000023c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000002ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000002e2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00000616
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0022067d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002206ee
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
Segmentation fault
meldroc@meldroc-laptop:~$  

```

---

### Post by meldroc on 2007-01-04
Bump...  Anyone encountered this issue?

---

### Post by Beini on 2007-01-06
> **meldroc said:**
> Bump...  Anyone encountered this issue?

Same problem without the dvdnav thing, I can bypass this by setting Disc Type to "DVD", not the default "DVD(menus)"

EDIT:

Fixed by building source of newer version of dvdnav4 from feisty repos

---

