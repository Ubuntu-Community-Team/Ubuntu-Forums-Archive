---
title: "Problems with VLC"
date: 2008-07-28
forum: Multimedia Software
---

### Post by hawk1278 on 2008-07-28
I am currently running HH.  I have gone through the steps to add the medibuntu repos and packages for dvd playback.  I have added the W32codecs. I noticed that Ubuntu is seeing my DVD drive as a CDROM drive.  I am able to play movies with MPlayer and Totem with out issue.  VLC seems to freeze up and crash every time I try to play a DVD with it.  I ran vlc from command line using vlc /media/cdrom and got the following:
VLC media player 0.8.6e Janus
starting VLC root wrapper... using UID 1000 (saturn)
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/saturn/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000007d9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000b69
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000bd9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00000bf7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000b16aa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000b8ad2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0035693d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003f786d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003f90fb
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[00000337] main private error: option glx-shm does not exist
[00000339] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  31 ()
  Serial number of failed request:  51
  Current serial number in output stream:  52
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb48a7767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb48a781e]
#2 /usr/lib/libX11.so.6 [0xb4a83518]
#3 /usr/lib/libX11.so.6(XESetCloseDisplay+0x31) [0xb4a668d1]
#4 /usr/lib/libGL.so.1 [0xb0c917c9]
#5 [0x8405010]

Any help/information would be much appreciated.

---

### Post by mc4man on 2008-07-28
You might try specifying a video output. Go to setting -> preferences -> on bottom right ck. show advanced options, on the left expand video and highlight output modules. In the drop down on the right pick from Xv, X11, or OpenGl.  (listed in order of preference) Make sure you click save between each attempt and try. Hopefully one of the three will work.

---

