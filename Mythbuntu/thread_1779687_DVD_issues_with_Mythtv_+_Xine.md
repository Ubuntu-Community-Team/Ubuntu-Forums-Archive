---
title: "DVD issues with Mythtv + Xine"
date: 2011-06-10
forum: Mythbuntu
---

### Post by Solicitous on 2011-06-10
Hi all, interesting problem that I am unable to find a solution for.  I am running Mythbuntu 10.04, which I recently updated Mythtv to 0.24 without hassle.  Where my issue lies is in playing some DVDs.

I am using Xine for playing the DVDs as I found a while ago many of the DVDs would not work with the Internal player.  I have been able to play DVDs without hassle since (purchased copyrighted DVDs with encryption). Last night however I tried to watch Transformers 2 DVD, which Xine would load then after 20-30 seconds throw me back to the Myth menu without error.  The logs produced were;

This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sdc1 mounted on / for CSS authentication
libdvdread: Could not open /dev/sdc1 with libdvdcss.
libdvdread: Can't open /dev/sdc1 for reading
libdvdread: Device /dev/sdc1 inaccessible, CSS authentication not available.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00001013
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000015b7
libdvdread: Elapsed time 22
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00001af7
libdvdread: Elapsed time 0
......
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x00350508
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x00352c62
libdvdread: Elapsed time 0
libdvdread: Found 14 VTS's
libdvdread: Elapsed time 25
Segmentation fault
2011-06-10 18:49:49.607 Unlocking input devices
2011-06-10 18:49:51.574 Locking input devices
(I skipped posting the middle section as it appears a repeat with no new information).

So for some reason a segmentation fault is occurring.  Xine will play other DVDs without hassle (such as Transformers 1).  I can take Transformers 2 DVD on the same machine and play is successfully (menus and all) through totem, which leads me to believe it isn't a libdvdcss issue.

So I can play all DVDs under totem, and now it appears only a few with Xine.  Any help would be appreciated with fixing Xine.

---

