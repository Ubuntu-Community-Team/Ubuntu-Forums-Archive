---
title: "Aaaaarrrrrggh DVD dilema"
date: 2008-07-25
forum: Multimedia Software
---

### Post by Midgetprawn on 2008-07-25
OK I have followed the various sticky's on setting up DVD/video applications. I have looked at [http://www.stchman.com/](http://www.stchman.com/) and followed that advice. I have even managed to watch the DVD (OK it's Fireman Sam and I have a 5 year old) but when I stop and try to play again I get badalloc warnings and it refuses to play. see ouputs below.

kjb@kjb-desktop:~$ vlc dvd:///dev/scd0 
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 45100C3F___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/kjb/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000143
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000069ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00006bb6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00006c03
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00008968
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000089b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000520ff
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0005214c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0009bab7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0009bb04
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000e5430
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x000e547d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0012ebaa
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0012ebf7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0017855f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x001785ac
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 2
[00000350] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000345] main decoder error: decoder is leaking pictures, resetting the heap
[00000346] main video output error: picture 0x8474ee8 refcount is -1
[00000346] main video output error: picture to date 0x8474ff4 has invalid status 6
[00000346] main video output error: picture to display 0x8474ff4 has invalid status 6
[00000346] main video output error: picture 0x8474ff4 refcount is -1
[00000345] main decoder error: decoder is leaking pictures, resetting the heap
[00000283] main playlist: stopping playback
kjb@kjb-desktop:~$ vlc dvd:///dev/scd0 
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 45100C3F___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/kjb/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000143
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000069ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00006bb6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00006c03
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00008968
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000089b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000520ff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0005214c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0009bab7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0009bb04
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000e5430
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x000e547d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0012ebaa
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0012ebf7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0017855f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x001785ac
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 2
[00000349] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86
kjb@kjb-desktop:~$ vlc dvd:///dev/scd0 
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 45100C3F___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/kjb/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000143
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000069ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00006bb6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00006c03
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00008968
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000089b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000520ff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0005214c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0009bab7
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0009bb04
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000e5430
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x000e547d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0012ebaa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0012ebf7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0017855f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x001785ac
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 1
[00000349] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  88
  Current serial number in output stream:  89

---

### Post by unoodles on 2008-07-25
I used to have lots of problems when using vlc, so I switched to xine. (sudo apt-get install xine)

---

### Post by Midgetprawn on 2008-07-25
Ta m8 but I have tried Gxine, mplayer, movie player and VLC and I get 2 steps forward and 1 back. Xine is currently playing sound track for menu screen with no picure!!

---

### Post by xc3RnbFO8P on 2008-07-25
Can you check if you this installed in Synaptic Package Manager:
> libdvdcss2   1.2.9-2 medibuntu4
libdvdread3  0.9.7-8buntu1
libdvdnav4    0.1.10-0.2

---

