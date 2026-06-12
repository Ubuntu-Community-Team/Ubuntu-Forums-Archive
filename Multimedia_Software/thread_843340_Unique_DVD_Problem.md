---
title: "Unique DVD Problem"
date: 2008-06-28
forum: Multimedia Software
---

### Post by eagledrc on 2008-06-28
Hey,

I have the Office Season 2 DVDs (four discs, all with 6 or so episodes on them).  I had some trouble watching them on my machine, but I finally stumbled upon a fix, so I watched the DVDs on Ubuntu.  I had already watched the 1st disc, so I inserted the 2nd and watched that over several days, taking it in and out and having no trouble.  When I was done with that and decided to watch the 3rd disc.  I watched most of it, then took it out to install a program via CD in WINE.  When I put the Office DVD back in to resume the watching, I got an error message on Totem (not the player I used to watch them; it pops up automatically) saying that "An error occurred.  Could not open location; you might not have permission to open the file."  When I try to open it with VLC, the player closes as soon as I click OK on the Open Menu Disc Dialog box.  Here is the Totem output from the terminal: ```
eagledrc@eagledrc-desktop:~$ totem
/home/eagledrc/.themes/snow-leopard-mac/gtk-2.0/gtkrc:41: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/eagledrc/.themes/snow-leopard-mac/gtk-2.0/gtkrc:42: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/eagledrc/.themes/snow-leopard-mac/gtk-2.0/gtkrc:43: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdread: Invalid IFO for title 1 (VTS_01_0.BUP).

(totem:7079): GStreamer-CRITICAL **: 
Trying to dispose element test_dvdsrc, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

```
And the GUI says: Totem could not play this media (DVD) although a plugin is present to handle it.  You might want to check that a disc is present in the drive and that it is correctly configured.
Here is the VLC output: ```
eagledrc@eagledrc-desktop:~$ vlc
VLC media player 0.8.6e Janus
/home/eagledrc/.themes/snow-leopard-mac/gtk-2.0/gtkrc:41: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/eagledrc/.themes/snow-leopard-mac/gtk-2.0/gtkrc:42: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/eagledrc/.themes/snow-leopard-mac/gtk-2.0/gtkrc:43: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: OFFICE
libdvdnav: DVD Serial Number: 34eeab72
libdvdnav: DVD Title (Alternative): S2_D3_R0
libdvdnav: Unable to find map file '/home/eagledrc/.dvdnav/OFFICE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000150
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00055444
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00058c71
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000cfe15
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000cfe19
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001ade04
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001ade08
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0021e358
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0021e35c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00304826
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0030482a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003a2167
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003a216b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003a436a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003a436e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003a5d78
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003a5d7c
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
libdvdread: Can't seek to block 349229
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed - CRASHING!!!
vlc: vm.c:198: ifoOpenNewVTSI: Assertion `0' failed.
Aborted

```
However, it works fine on Disc 2 whenever I insert it.  How can that be?  The disc plays fine on another computer running XP...

---

