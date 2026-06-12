---
title: "Mythbuntu 10.04 - MythVideo ISO play back not working."
date: 2010-05-02
forum: Mythbuntu
---

### Post by DemonBob on 2010-05-02
Guys, 

I did a fresh install of 10.04 today, since I was on 9.04 since it came out. Everything is working fine except for my IOS's that I have ripped previously. Mythfrontend log is below. libdvdcss2 is installed, along with mediabuntu codec's and ubuntu-restricted-extras. 

Any ideas?

```
2010-05-02 03:21:16.156 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-02 03:21:16.559 Registering Internal as a media playback plugin.
2010-05-02 03:21:16.584 Cannot load language en_us for module mytharchive
2010-05-02 03:21:16.610 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-02 03:21:16.610 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-02 03:21:16.611 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-02 03:21:16.611 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-05-02 03:21:16.612 Cannot load language en_us for module mythgallery
2010-05-02 03:21:16.615 Cannot load language en_us for module mythmovies
2010-05-02 03:21:16.631 Current MythMusic Schema Version (MusicDBSchemaVer): 101
7
2010-05-02 03:21:16.674 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma
,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-05-02 03:21:16.680 Cannot load language en_us for module mythmusic
2010-05-02 03:21:16.687 Current MythVideo Schema Version (mythvideo.DBSchemaVer)
: 1032
2010-05-02 03:21:16.713 Cannot load language en_us for module mythvideo
2010-05-02 03:21:16.719 Cannot load language en_us for module mythweather
2010-05-02 03:21:16.721 XMLParseBase: Loading window theme from /usr/share/mytht
v/themes/Mythbuntu/menu-ui.xml
2010-05-02 03:21:16.782 Loading menu theme from /usr/share/mythtv/themes/default
menu//mainmenu.xml
2010-05-02 03:21:16.785 Found mainmenu.xml for theme 'Mythbuntu'
2010-05-02 03:21:17.304 MythContext: Connecting to backend server: 192.168.30.3:
6543 (try 1 of 1)
2010-05-02 03:21:17.305 Using protocol version 56
2010-05-02 03:21:23.353 Loading menu theme from /usr/share/mythtv/themes/default
menu//library.xml
2010-05-02 03:21:25.470 XMLParseBase: Loading window theme from /usr/share/mytht
v/themes/Mythbuntu/video-ui.xml
2010-05-02 03:21:25.631 New DB connection, total: 2
2010-05-02 03:21:25.702 Connected to database 'mythconverg' at host: 192.168.30.
3
2010-05-02 03:21:27.479 XMLParseBase: Loading window theme from /usr/share/mytht
v/themes/Mythbuntu/video-ui.xml
2010-05-02 03:21:28.524 TV: Attempting to change from None to WatchingDVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version svnR1169
libdvdnav: vm: failed to open/read the DVD
2010-05-02 03:21:28.545 Failed to open DVD device at /dev/dvd
2010-05-02 03:27:49.187 TV: Attempting to change from None to WatchingDVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version svnR1169
libdvdnav: vm: failed to open/read the DVD
2010-05-02 03:27:49.196 Failed to open DVD device at /dev/dvd
demonbob@sys-mythtv:/var/log/mythtv$ 

```

---

### Post by tgm4883 on 2010-05-02
Are you using mythvideo storage groups?  [http://www.mythtv.org/wiki/MythVideo](http://www.mythtv.org/wiki/MythVideo)

---

### Post by DemonBob on 2010-05-02
Ah did not realize that made a difference. Can I just remove the video storage group and leave the path the same in video settings? Also leaching the other storage groups intact? I.e coverart and such?

---

### Post by DemonBob on 2010-05-02
Ok now I'm getting somewhere. Remove the SG, scan for changes, then try to play the movie. Now I am getting the erros below, for all ISO's which all worked fine on 9.04. I guess i am missing something important. 


```
/themes/Mythbuntu/video-ui.xml
2010-05-02 04:45:45.493 Unable to find image file: 1726_coverart.jpg
2010-05-02 04:45:46.533 TV: Attempting to change from None to WatchingDVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0004548b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000458a6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00045916
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000459f1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00048094
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000606be
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00071c15
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0033c9f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003c208d
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 2
libdvdnav: Using dvdnav version svnR1169
libdvdnav: DVD Title: IRON_MAN_DOM
libdvdnav: DVD Serial Number: 38F86801
libdvdnav: DVD Title (Alternative): IRON_MAN_DOM
libdvdnav: Unable to find map file '/home/demonbob/.dvdnav/IRON_MAN_DOM.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
2010-05-02 04:45:48.227 Opened DVD device at /media/mythtv/videos/IRON_MAN_DOM.i
so
2010-05-02 04:45:48.240 There are 18 titles on the disk
2010-05-02 04:45:48.240 Title 0 has 0 parts.
2010-05-02 04:45:48.240 Title 1 has 15 parts.
2010-05-02 04:45:48.240 Title 2 has 12 parts.
2010-05-02 04:45:48.240 Title 3 has 2 parts.
2010-05-02 04:45:48.240 Title 4 has 2 parts.
2010-05-02 04:45:48.241 Title 5 has 2 parts.
2010-05-02 04:45:48.241 Title 6 has 2 parts.
2010-05-02 04:45:48.241 Title 7 has 2 parts.
2010-05-02 04:45:48.241 Title 8 has 2 parts.
2010-05-02 04:45:48.241 Title 9 has 2 parts.
2010-05-02 04:45:48.241 Title 10 has 2 parts.
2010-05-02 04:45:48.241 Title 11 has 2 parts.
2010-05-02 04:45:48.241 Title 12 has 2 parts.
2010-05-02 04:45:48.241 Title 13 has 2 parts.
2010-05-02 04:45:48.241 Title 14 has 2 parts.
2010-05-02 04:45:48.241 Title 15 has 4 parts.
2010-05-02 04:45:48.241 Title 16 has 4 parts.
2010-05-02 04:45:48.241 Title 17 has 2 parts.
2010-05-02 04:45:48.434 AFD: Opened codec 0xb11be6e0, id(MPEG2VIDEO) type(Video)
2010-05-02 04:45:48.434 NVP(0): Disabling Audio, params(-1,-1,-1)
2010-05-02 04:45:48.617 VDPAU Error: Error at mythrender_vdpau.cpp:1448 (#1, Unk
nown)
2010-05-02 04:45:48.618 VDPAU Error: Failed to create VDPAU device.
2010-05-02 04:45:48.618 VDPAU Error: No VDPAU device
2010-05-02 04:45:48.618 Failed to create VDPAU render device.
2010-05-02 04:45:48.618 VidOutVDPAU Error: Failed to initialise VDPAU
2010-05-02 04:45:48.661 VideoOutputXv: Desired video renderer 'vdpau' not availa
ble.
			codec 'MPEG2' makes 'xv-blit,xshm,xlib,' available, usin
g 'xv-blit' instead.
2010-05-02 04:45:48.664 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-05-02 04:45:48.718 OSD Theme Dimensions W: 1280 H: 720
2010-05-02 04:45:49.305 TV: Changing from None to WatchingDVD
2010-05-02 04:45:49.328 Couldn't load deinterlace filter none
2010-05-02 04:45:49.333 Video timing method: USleep with busy wait
2010-05-02 04:45:49.385 Couldn't load deinterlace filter none
2010-05-02 04:45:49.385 Failed to enable deinterlacing
2010-05-02 04:45:49.424 AFD: Warning, video codec 0xb11be6e0 id(MPEG2VIDEO) type
 (Video) already open.
2010-05-02 04:45:49.641 AFD: codec AC3 has 0 channels
2010-05-02 04:45:49.642 AFD: Opened codec 0xaa0542d0, id(AC3) type(Audio)
2010-05-02 04:45:49.719 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 
0)
2010-05-02 04:45:49.719 Opening ALSA audio device 'default'.
2010-05-02 04:45:49.761 mixer unable to find control Master 1
2010-05-02 04:45:49.762 NVP(0): Enabling Audio
2010-05-02 04:45:49.762 [mpeg2video @ 0x1c63960]get_buffer() failed (stride chan
ged)
2010-05-02 04:45:49.763 AFD Error: Unknown decoding error
2010-05-02 04:45:49.763 [mpeg2video @ 0x1c63960]get_buffer() failed (stride chan
ged)
2010-05-02 04:45:49.763 AFD Error: Unknown decoding error
2010-05-02 04:45:49.763 [mpeg2video @ 0x1c63960]get_buffer() failed (stride chan
ged)
2010-05-02 04:45:49.763 AFD Error: Unknown decoding error
2010-05-02 04:45:49.763 [mpeg2video @ 0x1c63960]get_buffer() failed (stride chan
ged)
2010-05-02 04:45:49.763 AFD Error: Unknown decoding error
2010-05-02 04:45:49.764 [mpeg2video @ 0x1c63960]get_buffer() failed (stride chan
ged)
2010-05-02 04:45:49.764 AFD Error: Unknown decoding error
2010-05-02 04:45:49.764 [mpeg2video @ 0x1c63960]get_buffer() failed (stride chan
ged)
2010-05-02 04:45:49.764 AFD Error: Unknown decoding error
2010-05-02 04:45:49.769 [mpeg2video @ 0x1c63960]get_buffer() failed (stride chan
ged)
2010-05-02 04:45:49.769 AFD Error: Unknown decoding error
2010-05-02 04:45:49.769 [mpeg2video @ 0x1c63960]get_buffer() failed (stride chan
ged)
2010-05-02 04:45:49.769 AFD Error: Unknown decoding error
2010-05-02 04:45:49.770 [mpeg2video @ 0x1c63960]get_buffer() failed (stride chan
ged)
2010-05-02 04:45:49.770 AFD Error: Unknown decoding error

Rinse and Repeat error. 


```

---

### Post by iamlindoro on 2010-05-02
> **DemonBob said:**
> 
2010-05-02 04:45:49.769 AFD Error: Unknown decoding error
2010-05-02 04:45:49.770 [mpeg2video @ 0x1c63960]get_buffer() failed (stride chan
ged)
2010-05-02 04:45:49.770 AFD Error: Unknown decoding error

Rinse and Repeat error. 


You need to get set up with auto-builds and get to current .23-fixes rather than the shipping version-- this was solved a few weeks ago.

---

### Post by WIZARD DIO on 2010-05-02
try this 
  	 	 	 	 	 	  1 install VLC media player 
2 install Ubuntu restricted extra package from add/remove panel
3 go to terminal and type 
sudo apt-get install libdvdread4

4 on terminal again type 
sudo /usr/share/doc/libdvdread4/install-css.sh

put dvd into the drive and enjoy
:popcorn:

---

### Post by WIZARD DIO on 2010-05-02
1 install VLC media player 
2 install Ubuntu restricted extra package from add/remove panel
3 go to terminal and type 
sudo apt-get install libdvdread4

4 on terminal again type 
sudo /usr/share/doc/libdvdread4/install-css.sh

put dvd into the drive and enjoy
:popcorn:

---

