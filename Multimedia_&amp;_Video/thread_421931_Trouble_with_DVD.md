---
title: "Trouble with DVD"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by drstamm on 2007-04-24
I recently clean-installed Ubuntu 7.04.  I since have used Automatix to enable DVD playback.  Some DVDs will work well, but a few others will simply cause an error, regardless of which player or backend I use (so far I've tried totem-xine, totem-gstreamer, xine-ui, and VLC).  Totem displays "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?" even though I certainly have libdvdcss2 installed.  VLC simply halts, and xine (when run from the command line, displays
> 
[FONT="Courier New"]libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.[/FONT]

I'm not sure if it is a region setting (I don't think so because the behavior is so inconsistent among regions) or the DVD itself, (also doubted since it plays on a Windows computer).

I politely await your help.

---

### Post by will_in_wi on 2007-04-24
Could you install mplayer and try to run it and post the output?

The command is:
```

sudo apt-get install mplayer
mplayer dvd://

```

---

### Post by TheMono on 2007-04-24
What are the dvds that cause errors? New or old?

---

### Post by compiledkernel on 2007-04-25
See stickied link at the top. 

[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

---

### Post by Repent on 2007-04-26
Thats just fine but what do you do when you get this??

joe203@joe203-desktop:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
joe203@joe203-desktop:~$

---

### Post by mcarro on 2007-04-29
I am also having problems when trying to play (and to rip) encripted DVDs.  I have tried several versions of libdvdcss (libdvdcss2_1.2.7-2, libdvdcss2_1.2.9-1, and libdvdcss2_1.2.8-1) in combination with libdvdread3_0.9.4-5.1 and libdvdread3_0.9.4.7-2ubuntu1. The results are similar in all cases, so I do not know whether this is really a fault of dvdread and / or dvdcss. Anyway, here go the symptons. This is using libdvdread3_0.9.4.7-2ubuntu1 and 1.2.9-2medibuntu2+build1 and a system recently upgraded to Feisty (was plying OK in edgy). Xine returns these messages in the console:

---------------------------------------------------------------------------

This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000128
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000009c6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000009c6)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000541cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0039f3a8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0039f3a8)!!
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0

---------------------------------------------------------------------------

totem --debug does not show any debug message. A warning window appears stating that "Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it. Please install the necessary plugins and restart Totem to be able to play this media." Quite general.

gmplayer also fails, with the following error messages:

---------------------------------------------------------------------------

*** Zero check failed in ifo_read.c:1361
    for vts_tmapt->zero_1 = 0xbe08
*** Zero check failed in ifo_read.c:1535
    for c_adt->zero_1 = 0xcbb6

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1539 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1674 ***
*** for info_length % sizeof(uint32_t) == 0 ***

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1539 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000009c6)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0039f3a8)!!

---------------------------------------------------------------------------

They make me wonder whether the problem is in libdvdcss or in libdvdread

vlc, again. fails when trying to open the menus:

---------------------------------------------------------------------------

VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: PINK_PANTHER_SE_MAIN
libdvdnav: DVD Serial Number: 2edd45c3
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/mcarro/.dvdnav/PINK_PANTHER_SE_MAIN.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000128
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000009c6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000009c6)
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000541cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0039f3a8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0039f3a8)!!
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 3
libdvdnav: ifoRead_PGCI_UT failed - CRASHING!!!
vlc: vm.c:210: ifoOpenNewVTSI: Assertion `0' failed.

---------------------------------------------------------------------------

If I try to open the dvd in "simple" mode, thousands of errors as the one below appear:

---------------------------------------------------------------------------

*** Zero check failed in ifo_read.c:1361
    for vts_tmapt->zero_1 = 0x4b08
*** Zero check failed in ifo_read.c:1535
    for c_adt->zero_1 = 0xccb7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1539 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1567 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1569 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***

---------------------------------------------------------------------------

---

### Post by eejk on 2007-05-10
did anybody resolve their isssues??? I am having something similar with libdvdread: Invalid IFO for title 2

---

### Post by NotPhil on 2007-09-03
Try changing the DVD drive's region setting with [regionset.]("http://packages.ubuntu.com/feisty/utils/regionset")

---

### Post by ninja67 on 2007-11-13
I was able to apt-get install w32codecs libdvdcss2 when i was using feisty... but now i did a fresh install of  gutsy and I am not able to install those things... i guess there was  a repo medibuntu or something which no longer exists(?!)... does anybody know any alternate solution. 

i was happy when i had feisty coz mplayer would play any dvd.... now it doesn't play everything :((

---

### Post by ninja67 on 2007-11-13
hey found a solution ... that atleast works on my machine!!!

:) :)

add the next 2 lines to /etc/apt/sources.list

deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all

execute this command on the terminal

wget [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg) -O- | sudo apt-key add -

then do a 

sudo apt-get update
sudo apt-get upgrade

try using mplayer to play the dvd... if it doesn't work... do 

sudo apt-get install w32codecs
sudo apt-get installl libdvdcss2xxx-dev
sudo apt-get install libdvdreadxxx-dev

(note: xxx refers to whatever you get when you try to autocomplete while typing out the package name :) )
it must work. good luck!

i got the stuff from [http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

---

