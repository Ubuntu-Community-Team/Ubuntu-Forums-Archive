---
title: "DVD problems"
date: 2011-02-23
forum: Multimedia Software
---

### Post by Defolos on 2011-02-23
Hi,
I have a strange problem when I try to play "normal" DVDs. I followed  this guide:  [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) to  install the libdvdcss2 and installed the ubuntu-restricted-extras  package (dpkg tells me that they are both installed). Also the DVD-drive  is definitely working, as I tried with an unencrypted DVD. Problems  start when I try to play an encrypted one. I tried several players but  none of them will play a DVD. So I started them via console and here is  the output:
vlc:
```
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: 2001_A_SPACE_ODYSSEY
libdvdnav: DVD Serial Number: 386A7082
libdvdnav: DVD Title (Alternative): 2001_A_SPACE_ODYSSEY
libdvdnav: Unable to find map file '/home/dan/.dvdnav/2001_A_SPACE_ODYSSEY.map'
libdvdnav: DVD disk reports itself with Region mask 0x00e50000. Regions: 2 4 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000130
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000880
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00001c50
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0033565c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0033dc77
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003448f7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003449d5
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
Warning: call to srand(31427)
```totem:
wont play it at all, it just tells me that I need further plugins but is unable to find any.
kaffeine:
```
libdvdnav: Using dvdnav version 1.1.18.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: 2001_A_SPACE_ODYSSEY
libdvdnav: DVD Serial Number: 386A7082
libdvdnav: DVD Title (Alternative): 2001_A_SPACE_ODYSSEY
libdvdnav: Unable to find map file '/home/dan/.dvdnav/2001_A_SPACE_ODYSSEY.map'
libdvdnav: DVD disk reports itself with Region mask 0x00e50000. Regions: 2 4 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000130
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000880
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00001c50
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0033565c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0033dc77
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003448f7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003449d5
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
params.c:OpenConfFile() - Unable to open configuration file "/home/dan/.smb/smb.conf":
    No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/dan/.smb/smb.conf.append":
    No such file or directory
```I googled some of these errors and they seem to be typical for a missing  libdvdcss, what does not seem to be the case. Please tell me if you  have any ideas about missing plugins or packages.

---

