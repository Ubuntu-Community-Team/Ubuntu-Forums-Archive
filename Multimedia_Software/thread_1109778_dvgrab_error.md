---
title: "dvgrab error"
date: 2009-03-29
forum: Multimedia Software
---

### Post by Komir on 2009-03-29
For the first time I use dvgrab ( before windows user, now I "try" ubuntu), and now I have problem, after some time of capture I had error :

#
komir@komir-laptop:/media/disk/Stari$ sudo dvgrab -noavc -s 0 -showstatus -d 03:10:00 -f dv2 -nostop
Found AV/C device with GUID 0x08004601021fda7e
Turning on OpenDML to support large file size.
Capture Started
                                                                                 03:57:30
"dvgrab-001.avi": buffer underrun near: timecode 45:85:85.45 date 2009.03.29 03:57:30
This error means that the frames could not be written fast enough.
                                                                                 04:06:42
"dvgrab-001.avi": buffer underrun near: timecode 45:85:85.45 date 2009.03.29 04:06:42
This error means that the frames could not be written fast enough.
                                                                                 04:06:42
"dvgrab-001.avi": buffer underrun near: timecode 45:85:85.45 date 2009.03.29 04:06:42
This error means that the frames could not be written fast enough.
"dvgrab-001.avi":  1997.82 MiB 13806 frames timecode 45:85:85.45 date 2009.03.29 04:06:42Segmentation fault (core dumped)
#


I capture from VHS through Sony DCR-TRV223 PAL



Sorry for my english :redface:
Best regards from Croatia

---

