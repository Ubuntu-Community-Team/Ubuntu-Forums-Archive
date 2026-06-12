---
title: "One DVD plays, One DVD unreadable"
date: 2008-12-30
forum: Multimedia Software
---

### Post by pgmer6809 on 2008-12-30
Running Gutsy on Athlone 3200.
Insert a DVD created by a local outfit from an old 16mm film. It auto starts totem and plays fine.
Insert a second DVD created by the BBC from one of their old TV programs and the DVD main folder (VIDEO_TS) does not look like a folder, and cannot be opened. Tried as root and as myself. tried re-mounting etc. 
The DVD plays fine though under windows XP and in fact I can even use windows explorer to copy the files to hard disk. (there are about 9 of them and they total 1GB.)
After I copy the files to hard drive using XP, I can reboot into Ubuntu, and then I can play the video using totem by accessing the files on the hard drive. So the content etc is OK.

Anyone have any ideas as to what is missing/strange about this DVD?
Here are results of some tests.
888888888888888888888888888888888888888888888888888888888888888888888
root@shadow:/# lsdvd
*** Zero check failed in ifo_read.c:432
    for vmgi_mat->zero_3 = 0x00000000010000000000000000000000000000
Disc Title: DVD_VIDEO_RECORDER
Title: 01, Length: 00:23:14.000 Chapters: 05, Cells: 22, Audio streams: 01, Subpictures: 00

Title: 02, Length: 00:17:08.176 Chapters: 03, Cells: 17, Audio streams: 01, Subpictures: 00

Title: 03, Length: 00:16:41.176 Chapters: 04, Cells: 16, Audio streams: 01, Subpictures: 00

Longest track: 01
------------------------------------------------------------------------------------
ls -l dvd/VIDEO_TS/
total 1002018
-r--r--r-- 1 4294967295 4294967295     16384 2005-12-31 16:00 VIDEO_TS.BUP
-r--r--r-- 1 4294967295 4294967295     16384 2005-12-31 16:00 VIDEO_TS.IFO
-r--r--r-- 1 4294967295 4294967295     59392 2005-12-31 16:00 VIDEO_TS.VOB
-r--r--r-- 1 4294967295 4294967295     28672 2005-12-31 16:00 VTS_01_0.BUP
-r--r--r-- 1 4294967295 4294967295     28672 2005-12-31 16:00 VTS_01_0.IFO
-r--r--r-- 1 4294967295 4294967295 415543296 2005-12-31 16:00 VTS_01_1.VOB
-r--r--r-- 1 4294967295 4294967295     26624 2005-12-31 16:00 VTS_02_0.BUP
-r--r--r-- 1 4294967295 4294967295     26624 2005-12-31 16:00 VTS_02_0.IFO
-r--r--r-- 1 4294967295 4294967295 308736000 2005-12-31 16:00 VTS_02_1.VOB
-r--r--r-- 1 4294967295 4294967295     22528 2005-12-31 16:00 VTS_03_0.BUP
-r--r--r-- 1 4294967295 4294967295     22528 2005-12-31 16:00 VTS_03_0.IFO
-r--r--r-- 1 4294967295 4294967295 301539328 2005-12-31 16:00 VTS_03_1.VOB
------------------------------------------------------------------------------------------
root@shadow:/# mplayer dvd://1 
WIll using depmod to make a /etc/modules.listyer dvd://1
MPlayer 2:1.0~rc1-0ubuntu13.2+medibuntu1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 12, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
*** Zero check failed in ifo_read.c:432
    for vmgi_mat->zero_3 = 0x00000000010000000000000000000000000000
There are 3 titles on this DVD.
There are 5 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: unknown aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0

*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:207 ***
*** for dsi->dsi_gi.zero1 == 0 ***

MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9558.0 kbps (1194.8 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.


Exiting... (End of file)

---

