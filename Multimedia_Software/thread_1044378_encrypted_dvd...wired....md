---
title: "encrypted dvd...wired..."
date: 2009-01-19
forum: Multimedia Software
---

### Post by Til_Valhall_vi_drar! on 2009-01-19
hi, when i do:

dd if=/dev/hda of=/dev/zero

i get:

dd: reading `/dev/hda': Input/output error
3552+0 records in
3552+0 records out
1818624 bytes (1,8 MB) copied, 1,47158 seconds, 1,2 MB/s


-----------------------------------------------------------------------
i know this is because of its encrypted, i have libdvdcss2-dev installed

i can successfully rip other dvds with dd

the dvd is not damaged, it works under windowns.

the wired thing is; i tried using vlc, open /dev/hda as a file. then i got:

VLC media player 0.8.6c Janus
starting VLC root wrapper... using UID 0 (root)
***************************************
* Running VLC as root is discouraged. *
***************************************

 It is potentially dangerous, and might not even work properly.
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: EN_109955
libdvdnav: DVD Serial Number: 3FB8F2C5___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/root/.dvdnav/EN_109955.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000032a
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000397
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000d01
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000d24
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00000d71
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00000d8c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00000dd9
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0001403d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000163a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00041f68
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00041fb5
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000775c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0007760d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0008d272
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0008d2bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x000c5231
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x000c527e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x000db76f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x000e57f9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003471c2
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0034720f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00359507
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x00359554
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003913f5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x00391442
libdvdread: Elapsed time 1
libdvdread: Found 12 VTS's
libdvdread: Elapsed time 6
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  145 (MIT-SHM)
  Minor opcode of failed request:  1 (X_ShmAttach)
  Serial number of failed request:  49
  Current serial number in output stream:  50


------------------------------------------------------------------------
wait, i haven't got to the point yet... here it comes:

after i have tried with vlc, the dd command successfully rips the dvd...

so vlc must do something with the dvd... WHAT?? i have tried regionset, but i only successfully set it to region 2, at least thats what i got from output from the command.

so can someone tell me a command or give me a hint so i can to the same thing vlc does with the dvd?

sorry for my bad english...

---

