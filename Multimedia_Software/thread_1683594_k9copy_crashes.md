---
title: "k9copy crashes"
date: 2011-02-07
forum: Multimedia Software
---

### Post by MakOwner on 2011-02-07
k9copy is making me pull my hair out. What little I have left at any rate.

I'm trying to copy the Season 4 Southpark DVD's (These things came out in 2000 for christ's sake!) I just purchased onto my file server fo playback on the media player.  k9copy freezes up at 11 seconds into the menu of title set 2, then eventually crashes.

Anyone have a better native Linux/Ubuntu alternative to this .... wonderful application?  

Obviously this is not the first time it has crashed on me ....

k3b gives this in the debug output when trying to copy it - as soon as it hits the error it stops and deletes the output.


Devices
-----------------------
PIONEER DVD-RW  DVR-111D 1.23 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::DataTrackReader
-----------------------
reading sectors 0 to 2908967 with sector size 2048. Length: 2908968 sectors, 5957566464 bytes.
using buffer size of 128 blocks.
Problem while reading. Retrying from sector 2762525.
Read error in sector 2762525.
Read a total of 2762525 sectors (5657651200 bytes)

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.5 (KDE 4.4.5)
QT Version:  4.6.2
Kernel:      2.6.32-28-generic-pae


dvdbackup output:
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002e97
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00002f15
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0032274b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003247ad
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x003247ad)!!
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003247c3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00324819
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x00324819)!!
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 2



Anyone know how to force longer attempts at the keys?

---

