---
title: "DVD Playback - Bizarre codec problem"
date: 2007-12-22
forum: Mythbuntu
---

### Post by Titus A Duxass on 2007-12-22
Okay I've installed 7.10 and nearly everything works great, I love the mythstream setup.

The only problem I have is with DVD playback. I was watching a really old movie "The Osterman Weekend" from a DVD I got for free from a magazine.

Everything was okay until just before the very end of the film, xine stopped playback and said that I did not have enough rights to play this movie.

Xine also refuses to play my copy of "American Beauty".

I have all known codecs (w32codecs, libdvdcss) installed.

Is there something else I need to install. I have never had this problem with previous myth setups (6.10, debian, MythDora).

---

### Post by Titus A Duxass on 2008-01-19
Okay, I built another mythbox and have the same problem when trying to play American Beauty. This time I have a report from the terminal.


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdread: Can't allocate memory for file read!
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed
2008-01-19 14:11:35.122 There are 7 titles on the disk
2008-01-19 14:11:35.122 Title 0 has 0 parts.
2008-01-19 14:11:35.123 Title 1 has 29 parts.
2008-01-19 14:11:35.123 Title 2 has 2 parts.
2008-01-19 14:11:35.123 Title 3 has 2 parts.
2008-01-19 14:11:35.123 Title 4 has 1 parts.
2008-01-19 14:11:35.123 Title 5 has 2 parts.
2008-01-19 14:11:35.123 Title 6 has 2 parts.
libdvdnav: get_PGCN failed. Was trying to find pgcN in domain 2
libdvdnav: chapter NOT FOUND!
2008-01-19 14:11:35.130 DPMS Deactivated 
2008-01-19 14:11:35.172 DVDNAV_STOP
2008-01-19 14:11:35.209 NVP::OpenFile(): Error, couldn't read file: 
//dev/dvd
2008-01-19 14:11:35.239 TV Error: StartPlayer(): NVP is not playing 
after 20000 msec
2008-01-19 14:11:35.269 TV: Changing from None to WatchingPreRecorded
2008-01-19 14:11:35.270 TV: Attempting to change from 
WatchingPreRecorded to None
2008-01-19 14:11:35.272 TV: Changing from WatchingPreRecorded to None
2008-01-19 14:11:36.279 DPMS Reactivated.

---

### Post by superm1 on 2008-01-19
> **Titus A Duxass said:**
> Okay, I built another mythbox and have the same problem when trying to play American Beauty. This time I have a report from the terminal.


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdread: Can't allocate memory for file read!
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed
2008-01-19 14:11:35.122 There are 7 titles on the disk
2008-01-19 14:11:35.122 Title 0 has 0 parts.
2008-01-19 14:11:35.123 Title 1 has 29 parts.
2008-01-19 14:11:35.123 Title 2 has 2 parts.
2008-01-19 14:11:35.123 Title 3 has 2 parts.
2008-01-19 14:11:35.123 Title 4 has 1 parts.
2008-01-19 14:11:35.123 Title 5 has 2 parts.
2008-01-19 14:11:35.123 Title 6 has 2 parts.
libdvdnav: get_PGCN failed. Was trying to find pgcN in domain 2
libdvdnav: chapter NOT FOUND!
2008-01-19 14:11:35.130 DPMS Deactivated 
2008-01-19 14:11:35.172 DVDNAV_STOP
2008-01-19 14:11:35.209 NVP::OpenFile(): Error, couldn't read file: 
//dev/dvd
2008-01-19 14:11:35.239 TV Error: StartPlayer(): NVP is not playing 
after 20000 msec
2008-01-19 14:11:35.269 TV: Changing from None to WatchingPreRecorded
2008-01-19 14:11:35.270 TV: Attempting to change from 
WatchingPreRecorded to None
2008-01-19 14:11:35.272 TV: Changing from WatchingPreRecorded to None
2008-01-19 14:11:36.279 DPMS Reactivated.
Try installing the regionset utility, and verify the region that you have set.  It's in apt.

---

### Post by Titus A Duxass on 2008-01-20
Thanks, that solved it.
Simply installing the package cured the problem.

---

### Post by Titus A Duxass on 2008-01-27
Well, it happened again.
This time the system (mythbuntu or xine?) elects not to play The Bourne Ultimatum.

This is from the terminal when using xine:
paul@mythbox:~$ mythfrontend
2008-01-27 10:42:35.690 Using runtime prefix = /usr
2008-01-27 10:42:35.699 Gnome-Screensaver support enabled
2008-01-27 10:42:35.700 DPMS is active.
2008-01-27 10:42:35.712 New DB connection, total: 1
2008-01-27 10:42:35.720 Connected to database 'mythconverg' at host:
localhost
2008-01-27 10:42:35.721 Total desktop dim: 800x600, with 1 screen[s].
2008-01-27 10:42:35.724 Using screen 0, 800x600 at 0,0
2008-01-27 10:42:35.733 Current Schema Version: 1160
2008-01-27 10:42:35.735 mythfrontend version: 0.20.20070821-1
[www.mythtv.org](www.mythtv.org)
2008-01-27 10:42:35.735 Enabled verbose msgs:  important general
2008-01-27 10:42:36.113 Total desktop dim: 800x600, with 1 screen[s].
2008-01-27 10:42:36.114 Using screen 0, 800x600 at 0,0
2008-01-27 10:42:36.115 Switching to square mode (Mythbuntu)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
2008-01-27 10:42:36.122 Using the Qt painter
Xlib:  extension "GLX" missing on display ":0.0".
mythtv: could not connect to socket
mythtv: Connection refused
lirc_init failed for mythtv, see preceding messages
2008-01-27 10:42:36.260 Joystick disabled.
2008-01-27 10:42:36.390 Loading from:
/usr/share/mythtv/themes/Mythbuntu/base.xml
2008-01-27 10:42:36.410 Loading from:
/usr/share/mythtv/themes/default/base.xml
2008-01-27 10:42:36.489 Registering Internal as a media playback
plugin.
2008-01-27 10:42:36.515 Registering MythDVD DVD Media Handler as a
media handler ext()
2008-01-27 10:42:36.526 Mediamonitor: Adding /dev/hdc
2008-01-27 10:42:36.534 Mediamonitor: AddDevice() -- Not adding
'/dev/hdc', it appears to be a duplicate.
2008-01-27 10:42:36.536 Registering MythDVD VCD Media Handler as a
media handler ext()
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2008-01-27 10:42:36.654 Registering MythMusic Media Handler 1/2 as a
media handler ext()
2008-01-27 10:42:36.654 Registering MythMusic Media Handler 2/2 as a
media handler ext(ogg,mp3,aac,flac)
2008-01-27 10:42:36.654 MonitorRegisterExtensions(0x40,
ogg,mp3,aac,flac)
2008-01-27 10:42:36.716 Starting media monitor.
2008-01-27 10:42:37.541 Media status changed...  New status is:
MEDIASTAT_USEABLE old status was MEDIASTAT_NOTMOUNTED
2008-01-27 10:42:37.541 Posting MediaEvent
2008-01-27 10:42:37.692 Found a handler
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.
Xlib:  extension "GLX" missing on display ":0.0".
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hda1 mounted on / for CSS
authentication
libdvdread: Could not open /dev/hda1 with libdvdcss.
libdvdread: Can't open /dev/hda1 for reading
libdvdread: Device /dev/hda1 inaccessible, CSS authentication not
available.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000006b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001a573
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002d54d0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002d54d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e485d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e4862
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00314f01
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00314f06
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00373aa8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00373aae
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003d5963
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003d5968
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003d7ff4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003d7ff9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003d9a20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003d9a26
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0001a573
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
AFD changed from -2 to -1
Segmentation fault (core dumped)

And this from the terminal when using the internal player:


2008-01-27 10:45:49.322 Connected to database 'mythconverg' at host:
localhost
QDate::fromString: Parameter out of range
2008-01-27 10:45:49.372 TV: Attempting to change from None to
WatchingPreRecorded
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: BOURNE_ULTIMATUM
libdvdnav: DVD Serial Number: 377a9503
libdvdnav: DVD Title (Alternative): G4_R1
libdvdnav: Unable to find map file
'/home/paul/.dvdnav/BOURNE_ULTIMATUM.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000.
Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000006b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001a573
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002d54d0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002d54d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e485d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e4862
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00314f01
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00314f06
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00373aa8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00373aae
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003d5963
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003d5968
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003d7ff4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003d7ff9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003d9a20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003d9a26
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0001a573
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
2008-01-27 10:45:50.068 Opened DVD device at //dev/dvd
2008-01-27 10:45:50.068 There are 22 titles on the disk
2008-01-27 10:45:50.068 Title 0 has 0 parts.
2008-01-27 10:45:50.069 Title 1 has 21 parts.
2008-01-27 10:45:50.069 Title 2 has 1 parts.
2008-01-27 10:45:50.069 Title 3 has 1 parts.
2008-01-27 10:45:50.069 Title 4 has 2 parts.
2008-01-27 10:45:50.069 Title 5 has 2 parts.
2008-01-27 10:45:50.069 Title 6 has 2 parts.
2008-01-27 10:45:50.069 Title 7 has 2 parts.
2008-01-27 10:45:50.069 Title 8 has 9 parts.
2008-01-27 10:45:50.069 Title 9 has 2 parts.
2008-01-27 10:45:50.069 Title 10 has 2 parts.
2008-01-27 10:45:50.069 Title 11 has 2 parts.
2008-01-27 10:45:50.069 Title 12 has 2 parts.
2008-01-27 10:45:50.069 Title 13 has 2 parts.
2008-01-27 10:45:50.069 Title 14 has 6 parts.
2008-01-27 10:45:50.070 Title 15 has 2 parts.
2008-01-27 10:45:50.070 Title 16 has 2 parts.
2008-01-27 10:45:50.070 Title 17 has 2 parts.
2008-01-27 10:45:50.070 Title 18 has 2 parts.
2008-01-27 10:45:50.070 Title 19 has 2 parts.
2008-01-27 10:45:50.070 Title 20 has 2 parts.
2008-01-27 10:45:50.070 Title 21 has 2 parts.
2008-01-27 10:45:50.078 DPMS Deactivated
2008-01-27 10:45:50.574 AFD: Opened codec 0x938d8f0, id(MPEG2VIDEO)
type(Video)
2008-01-27 10:45:50.641 NVP: Disabling Audio, params(-1,-1,-1)
2008-01-27 10:45:50.642 NVP: Disabling Audio, params(0,-1,-1)
2008-01-27 10:45:50.683 VideoOutputXv: XvMCTex: Init failed
2008-01-27 10:45:50.713 VideoOutputXv Error: Could not find suitable
XVideo surface.
2008-01-27 10:45:50.713 VideoOutputXv: Falling back to X shared
memory video output.
                              *** May be slow ***
2008-01-27 10:45:51.917 TV: Changing from None to WatchingPreRecorded
2008-01-27 10:45:51.922 VideoOutputXv Error: GetRefreshRate(): X11
ModeLine query returned zeroes
2008-01-27 10:45:51.994 VideoOutputXv Error: GetRefreshRate(): X11
ModeLine query returned zeroes
2008-01-27 10:45:51.994 Video timing method: USleep with busy wait
2008-01-27 10:45:53.688 AFD: Warning, video codec 0x938d8f0
id(MPEG2VIDEO) type (Video) already open.
2008-01-27 10:45:53.745 AFD: Opened codec 0xaf81f60, id(AC3)
type(Audio)
2008-01-27 10:45:53.762 Opening ALSA audio device 'default'.
2008-01-27 10:45:53.872 NVP: Enabling Audio
2008-01-27 10:45:54.068 AO: dropping back audio_buffer_unused
2008-01-27 10:45:54.156 AO: dropping back audio_buffer_unused
2008-01-27 10:45:54.328 AO: dropping back audio_buffer_unused
2008-01-27 10:45:54.427 AO: dropping back audio_buffer_unused
2008-01-27 10:45:54.545 AO: dropping back audio_buffer_unused
2008-01-27 10:45:54.633 AO: dropping back audio_buffer_unused
2008-01-27 10:45:54.723 AO: dropping back audio_buffer_unused
2008-01-27 10:45:54.754 AO: dropping back audio_buffer_unused
2008-01-27 10:45:54.820 AO: dropping back audio_buffer_unused
2008-01-27 10:45:54.911 AO: dropping back audio_buffer_unused
2008-01-27 10:45:54.943 AO: dropping back audio_buffer_unused
2008-01-27 10:45:55.005 AO: dropping back audio_buffer_unused
2008-01-27 10:45:55.010 AO: dropping back audio_buffer_unused
2008-01-27 10:45:55.105 AO: dropping back audio_buffer_unused
2008-01-27 10:45:55.232 AO: dropping back audio_buffer_unused
2008-01-27 10:45:55.263 AO: dropping back audio_buffer_unused
2008-01-27 10:46:16.402 AFD: Warning, video codec 0x938d8f0
id(MPEG2VIDEO) type (Video) already open.
2008-01-27 10:46:16.402 AFD: Warning, audio codec 0xaf81f60 id(AC3)
type (Audio) already open, leaving it alone.
2008-01-27 10:46:16.402 AFD: Opened codec 0xb0e1320, id(DVD_SUBTITLE)
type(Subtitle)
2008-01-27 10:46:16.403 AFD: Warning, audio codec 0xaf81f60 id(AC3)
type (Audio) already open, leaving it alone.
2008-01-27 10:46:16.405 AFD: Warning, video codec 0x938d8f0
id(MPEG2VIDEO) type (Video) already open.
2008-01-27 10:46:16.405 AFD: Warning, audio codec 0xaf81f60 id(AC3)
type (Audio) already open, leaving it alone.
2008-01-27 10:46:16.405 AFD: Opened codec 0xaf273c0, id(DVD_SUBTITLE)
type(Subtitle)
2008-01-27 10:46:26.580 AFD: Warning, audio codec 0xaf81f60 id(AC3)
type (Audio) already open, leaving it alone.
[mpeg2video @ 0xb7318ce8]ac-tex damaged at 20 10
[mpeg2video @ 0xb7318ce8]Warning MVs not available
2008-01-27 10:46:31.107 AFD: Warning, audio codec 0xaf81f60 id(AC3)
type (Audio) already open, leaving it alone.
2008-01-27 10:46:31.296 WriteAudio: buffer underrun
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed
2008-01-27 10:46:48.388 DVDNAV_STOP
2008-01-27 10:46:48.457 TV: Attempting to change from
WatchingPreRecorded to None
2008-01-27 10:46:48.483 TV: Changing from WatchingPreRecorded to None
2008-01-27 10:46:49.484 DPMS Reactivated.
2008-01-27 10:46:51.185 Connecting to backend server: 127.0.0.1:6543
(try 1 of 5)
2008-01-27 10:46:51.186 Using protocol version 31

---

### Post by Titus A Duxass on 2008-01-27
An update - I did a clean install of MythDora on another machine and got the same problems. So it is not Mythbuntu, but something relating to the DVD. Is this new encoding or something like?

The failure with dora was:    libdvdnav:ifoREAD_VOBU_ADMAP vtsi failed.

---

### Post by stdPikachu on 2008-01-27
Googling that error message shows it's a new form of copy protection designed to stop pesky thieving pirates like yourself from stealing DVD's. Why do you hate America? Pay for your films, you low-life commie!

[http://lists.mplayerhq.hu/pipermail/mplayer-advusers/2007-August/001720.html](http://lists.mplayerhq.hu/pipermail/mplayer-advusers/2007-August/001720.html)

Not run into that message myself yet though I imagine there's still time. Yay for paying customers being deliberately treated like ****.

[http://www.youtube.com/watch?v=MTbX1aMajow](http://www.youtube.com/watch?v=MTbX1aMajow)

---

### Post by Titus A Duxass on 2008-01-28
A new form of protection, I thought as much.
Got again last night whilst trying to play the Fantastic Four.

I had to did out an old DVD player (circa. 8yr old) and use that. Incredible an old machine can play them without problem.

---

### Post by Titus A Duxass on 2008-01-28
Sorry, I cannot checked the keyboard problem on my new system.
The motherboard (ASRock K8NF6P-VSTA) with on-board nvidia graphics (6100) gives me an out of frequency failure during install in both normal and safe graphics mode.

---

### Post by superm1 on 2008-01-28
> **Titus A Duxass said:**
> Sorry, I cannot checked the keyboard problem on my new system.
The motherboard (ASRock K8NF6P-VSTA) with on-board nvidia graphics (6100) gives me an out of frequency failure during install in both normal and safe graphics mode.
Once X boots up, try:

<ctrl><alt><-> and <ctrl><alt><+> to change resolutions that X might be able to use.

---

### Post by Titus A Duxass on 2008-01-29
Sorry I posted that on the wrong thread. I will provide any answers back on my other thread.

---

### Post by Titus A Duxass on 2008-02-29
Okay, the saga continues.
I'm back using a 7.10 based Mythbuntu install.
The dvd playback problem get worse, it now dumps in the middle of films that it played perfectly 2 or 3 weeks ago.

What logs or reports should I look at and can I view by shhing in from another machine?

---

### Post by yahooadam on 2008-03-30
im getting the problem trying to play the matrix on my box

```
2008-03-30 06:43:32.137 TV: Attempting to change from None to WatchingPreRecorded
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: THE_MATRIX
libdvdnav: DVD Serial Number: xxxxxxxxx
libdvdnav: DVD Title (Alternative): THE_MATRIX
libdvdnav: Unable to find map file '/home/adam/.dvdnav/THE MATRIX.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00058a70
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00058b93
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000c190b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000c86d8
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0035a1a8
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 1
2008-03-30 06:43:33.435 Opened DVD device at //dev/dvd
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
2008-03-30 06:43:33.436 There are 37 titles on the disk
2008-03-30 06:43:33.436 Title 0 has 0 parts.
2008-03-30 06:43:33.437 Title 1 has 38 parts.
2008-03-30 06:43:33.437 Title 2 has 1 parts.
2008-03-30 06:43:33.437 Title 3 has 2 parts.
2008-03-30 06:43:33.437 Title 4 has 2 parts.
2008-03-30 06:43:33.437 Title 5 has 2 parts.
2008-03-30 06:43:33.437 Title 6 has 38 parts.
2008-03-30 06:43:33.437 Title 7 has 3 parts.
2008-03-30 06:43:33.438 Title 8 has 3 parts.
2008-03-30 06:43:33.438 Title 9 has 1 parts.
2008-03-30 06:43:33.438 Title 10 has 2 parts.
2008-03-30 06:43:33.438 Title 11 has 2 parts.
2008-03-30 06:43:33.438 Title 12 has 1 parts.
2008-03-30 06:43:33.438 Title 13 has 38 parts.
2008-03-30 06:43:33.438 Title 14 has 38 parts.
2008-03-30 06:43:33.438 Title 15 has 99 parts.
2008-03-30 06:43:33.438 Title 16 has 2 parts.
2008-03-30 06:43:33.439 Title 17 has 2 parts.
2008-03-30 06:43:33.439 Title 18 has 2 parts.
2008-03-30 06:43:33.439 Title 19 has 1 parts.
2008-03-30 06:43:33.439 Title 20 has 1 parts.
2008-03-30 06:43:33.439 Title 21 has 1 parts.
2008-03-30 06:43:33.439 Title 22 has 1 parts.
2008-03-30 06:43:33.439 Title 23 has 1 parts.
2008-03-30 06:43:33.440 Title 24 has 1 parts.
2008-03-30 06:43:33.440 Title 25 has 1 parts.
2008-03-30 06:43:33.440 Title 26 has 1 parts.
2008-03-30 06:43:33.440 Title 27 has 1 parts.
2008-03-30 06:43:33.440 Title 28 has 1 parts.
2008-03-30 06:43:33.440 Title 29 has 1 parts.
2008-03-30 06:43:33.440 Title 30 has 1 parts.
2008-03-30 06:43:33.440 Title 31 has 1 parts.
2008-03-30 06:43:33.440 Title 32 has 1 parts.
2008-03-30 06:43:33.440 Title 33 has 1 parts.
2008-03-30 06:43:33.441 Title 34 has 1 parts.
2008-03-30 06:43:33.441 Title 35 has 1 parts.
2008-03-30 06:43:33.441 Title 36 has 1 parts.
libdvdnav: get_PGCN failed. Was trying to find pgcN in domain 2
libdvdnav: chapter NOT FOUND!
2008-03-30 06:43:33.475 DVDNAV_STOP
2008-03-30 06:43:33.475 NVP::OpenFile(): Error, couldn't read file: //dev/dvd
2008-03-30 06:43:33.475 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-03-30 06:43:33.475 TV: Changing from None to WatchingPreRecorded
2008-03-30 06:43:33.478 TV: Attempting to change from WatchingPreRecorded to None
2008-03-30 06:43:33.479 TV: Changing from WatchingPreRecorded to None
2008-03-30 06:43:34.621 DPMS Deactivated
2008-03-30 06:43:34.622 DPMS Reactivated.
```

---

### Post by Titus A Duxass on 2008-05-17
This has raised its ugly head again.
Whilst trying to play an old DVD (the whole nine yards) first I get a failure message "failed to mount" and the logfile is constantly giving:
2008-05-17 16:00:06.774 DPMS Reactivated.
2008-05-17 16:00:06.775 DPMS Deactivated 
2008-05-17 16:00:06.875 DPMS Reactivated.
2008-05-17 16:00:06.876 DPMS Deactivated 
2008-05-17 16:00:06.876 DPMS Reactivated.
2008-05-17 16:00:06.876 DPMS Deactivated 

Until I Ctrl+C it.

The system freezes and I have C+A+backspace to restart x.

Rebooting does not solve it, regionset is installed.

---

