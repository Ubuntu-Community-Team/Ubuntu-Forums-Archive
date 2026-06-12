---
title: "MythDVD fails about halfway."
date: 2008-01-17
forum: Mythbuntu
---

### Post by Scrier on 2008-01-17
Hi,

I have tried ripping 2 movies now and it stops halfways on perfect and on iso file. Not sure im missing some settings.  here is the out put from the terminal:
> libdvdread: Using libdvdcss version 1.2.5 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000015d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00017726
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0019366d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001936bb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0019c889
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0019c8d7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001a76b2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001a7700
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001db46d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001db4bb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x001ec039
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001ec087
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x001ed59e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x001ed5ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x001f01d9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x001f0227
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x001f2e14
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x001f2e62
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x001f63e6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x001f6434
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x001f8716
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x001f8764
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x001fbf13
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x001fbf61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x00201f48
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x00201f96
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x0020665e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x002066ac
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x0020af5f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x0020afad
libdvdread: Elapsed time 0
libdvdread: Found 15 VTS's
libdvdread: Elapsed time 0
2008-01-17 18:22:08.647 Ripfile tried to write 479232 bytes, but only managed to write 235519

And here is the mtd log:
> mtd started at Thu Jan 17 18:03:14 2008
mtd is running on a host called frontend1
18:03:14: Waiting for connections/jobs
18:03:14: mtd is listening on port 2442
18:03:18: DVD inserted: SAMURAI_X_2_082800
18:03:18:             : Title 1 is of type 4 (dvdinput table)
18:03:18:             : Title 2 is of type 4 (dvdinput table)
18:03:18:             : Title 3 is of type 4 (dvdinput table)
18:03:18:             : Title 4 is of type 4 (dvdinput table)
18:03:18:             : Title 5 is of type 4 (dvdinput table)
18:03:18:             : Title 6 is of type 4 (dvdinput table)
18:03:18:             : Title 7 is of type 4 (dvdinput table)
18:03:18:             : Title 8 is of type 4 (dvdinput table)
18:03:18:             : Title 9 is of type 4 (dvdinput table)
18:03:18:             : Title 10 is of type 4 (dvdinput table)
18:03:18:             : Title 11 is of type 4 (dvdinput table)
18:03:18:             : Title 12 is of type 4 (dvdinput table)
18:03:18:             : Title 13 is of type 4 (dvdinput table)
18:03:18:             : Title 14 is of type 4 (dvdinput table)
18:03:18:             : Title 15 is of type 4 (dvdinput table)
18:03:30: a client socket has been opened
18:04:00: launching job: job dvd 1 2 -1 0 0 /media-files/anime/SAMURAI_X_2_082800
18:04:00: Using DVD source: /dev/dvd
18:04:00: ISO DVD image copy to: /media-files/anime/SAMURAI_X_2_082800_001of
18:11:06: Error: DVDISOCopyThread rip file write error
18:11:08: job failed: job dvd 1 2 -1 0 0 /media-files/anime/SAMURAI_X_2_082800
18:11:14: a client socket has been closed
18:14:00: a client socket has been opened
18:14:30: launching job: job dvd 1 2 0 0 0 /media-files/anime/SAMURAI_X_2_082800
18:14:30: job thread beginning to rip dvd title
18:22:08: Error: Couldn't write blocks during a rip. Filesystem size exceeded? Disc full?
18:22:10: job failed: job dvd 1 2 0 0 0 /media-files/anime/SAMURAI_X_2_082800

I have started the daemon manually after boot as I havent gotten it to work with startup at boot time yet.

---

### Post by Alfaroid on 2008-01-17
> **Scrier said:**
> 
18:04:00: ISO DVD image copy to: /media-files/anime/SAMURAI_X_2_082800_001of

Do you read and write permissions to the folder above?

---

### Post by Scrier on 2008-01-17
Hmm seems I have write priviliges there, although according to the settings in mythtv I should be writing the file to /var/lib/mythdvd/temp

---

### Post by Scrier on 2008-01-18
Hmm, think it's solved now. The /media-files/anime/ folder is a shared samba mount so I need to add lfs in the fstab. 

Although this still raises the question why it sets /media-files/anime/ as target for the rip, as the only folder I have set is the temporary files to /var/lib/mythdvd/temp/, Is there some setting here that I can set to store the images locally first or do I get this because of the stored media files in MythVideo plugin?

---

### Post by Scrier on 2008-01-18
Apparently the first directory you put in the MythVideo setting is the one that the dvd is stored to.

---

