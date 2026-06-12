---
title: "DVD Playback not working on some DVDs"
date: 2008-06-06
forum: Multimedia Software
---

### Post by MrHyde on 2008-06-06
Hi,

I've got MythTV mostly working under Gutsy Gibbon, but the DVD playback has been giving me lots of trouble.  It seems about 90% of the DVDs that I have just do not work and I have not no idea why?  The output from the log in the mythfrontend.log file is pasted below.

[PHP]
QDate::fromString: Parameter out of range
2008-06-07 12:36:16.265 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.5 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000082a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00026604
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00287d27
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00287d85
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002da241
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002df003
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003684ed
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: DVD Title: YUNHOTATOHKYAHOTA_SCN
libdvdnav: DVD Serial Number: 350356ea
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/mythtv/.dvdnav/YUNHOTATOHKYAHOTA_SCN.map'
libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8
2008-06-07 12:36:16.359 Opened DVD device at //dev/dvd
libdvdread: Can't seek to block 3572965
libdvdread: Invalid IFO for title 4 (VTS_04_0.IFO).
libdvdnav: ifoOpenVTSI failed
2008-06-07 12:36:16.359 There are 9 titles on the disk
2008-06-07 12:36:16.359 Title 0 has 0 parts.
2008-06-07 12:36:16.359 Title 1 has 19 parts.
2008-06-07 12:36:16.359 Title 2 has 3 parts.
2008-06-07 12:36:16.359 Title 3 has 7 parts.
2008-06-07 12:36:16.359 Title 4 has 2 parts.
2008-06-07 12:36:16.359 Title 5 has 8 parts.
2008-06-07 12:36:16.359 Title 6 has 1 parts.
2008-06-07 12:36:16.359 Title 7 has 1 parts.
2008-06-07 12:36:16.359 Title 8 has 1 parts.
2008-06-07 12:36:16.361 DPMS Deactivated
2008-06-07 12:36:16.450 DVDNAV_STOP
2008-06-07 12:36:16.469 NVP::OpenFile(): Error, couldn't read file: //dev/dvd
2008-06-07 12:36:16.473 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-06-07 12:36:16.473 TV: Changing from None to WatchingPreRecorded
2008-06-07 12:36:16.477 TV: Attempting to change from WatchingPreRecorded to None
2008-06-07 12:36:16.477 TV: Changing from WatchingPreRecorded to None
2008-06-07 12:36:17.501 DPMS Reactivated.

[/PHP]

I can see a line say it can't read //dev/dvd, but I don't know why.  It was able to determine the DVD title and how many chapters it has and that should only be possible if it can read the dvd.

Cheers and thanks in advance

Vivek

---

