---
title: "DVD Movies"
date: 2009-01-30
forum: Multimedia Software
---

### Post by theozzlives on 2009-01-30
I have 4 computers on my network. I have the codecs for playing movies installed the same on all computers (except the one that won't play I installed thr gstreamer codecs before I remembered the restricted extras). On one (no matter what player I use) I get a wide pink line and garbage on each side.

This is the computer that houses my Apache Server so it's really not that important, but I might wanna watch Girls Gone Wild. Anyhoo I like everything to work right. Any ideas?

---

### Post by steeleyuk on 2009-01-30
Have you installed libdvdcss2?

---

### Post by theozzlives on 2009-01-30
yes

---

### Post by Neural oD on 2009-01-30
strange - try starting your players from the command line - and see if there's any useful output.

---

### Post by theozzlives on 2009-01-30
here's the text:
```
ozzie@ubuntu-server:~$ totem-xine
** (totem-xine:20671): DEBUG: Init of Python module
** (totem-xine:20671): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem-xine:20671): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem-xine:20671): DEBUG: Creating Python plugin instance
** (totem-xine:20671): DEBUG: Init of Python module
** (totem-xine:20671): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem-xine:20671): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem-xine:20671): DEBUG: Creating Python plugin instance
** Message: no file info
libdvdnav: Using dvdnav version 1.1.15 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: GIRLS_GONE_WILD
libdvdnav: DVD Serial Number: 371034BBC8EFCB44
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ozzie/.dvdnav/GIRLS_GONE_WILD.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000198
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000073df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0019b8f4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0019b92d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0019b954
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0019b98d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0019b9b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0019b9ed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0019c85d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0019c896
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0019fa00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0019fa39
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
** (totem-xine:20671): DEBUG: Finalizing Python plugin instance
** (totem-xine:20671): DEBUG: Finalizing Python plugin instance
ozzie@ubuntu-server:~$ 

```

---

