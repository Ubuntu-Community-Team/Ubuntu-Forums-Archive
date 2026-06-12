---
title: "vlc gives errors when trying to play encrypted dvd"
date: 2008-06-22
forum: Multimedia Software
---

### Post by TheRingmaster on 2008-06-22
I get this error when I try to play an encrypted dvd (king kong) in vlc. i do have libdvdcss installed. 

> donald@donald-desktop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: KING_KONG
libdvdnav: DVD Serial Number: 34319658
libdvdnav: DVD Title (Alternative): FULLFRAME_R1
libdvdnav: Unable to find map file '/home/donald/.dvdnav/KING_KONG.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000004c3
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000004c3)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000fdca
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000fdca)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003dcbfe
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003dcc02
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003ea942
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003ea946
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 1
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted


---

### Post by mc4man on 2008-06-22
Do you know if a region has been set on your drive? If your not sure install regionset and with a _dvd in the drive_ run regionset. here is ex. of a set drive
```
oug@doug-desktop:~$ regionset 
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET     [COLOR="Red"]<-[/COLOR]
vendor resets available: 4
user controlled changes resets available: 
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]: n
```
If it wasn't set set it to region 1 and before trying playback go home folder (show hidden folders), find .dvdcss and delete any folders inside.
If it _was set_ exit out answering no or is you still don't have playback then post back.
Or try the 
```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
``` some systems need to use an earlier version of libdvdcss2

---

