---
title: "pc freeze when i play dvd"
date: 2008-11-06
forum: Multimedia Software
---

### Post by orphen974 on 2008-11-06
hi,

Ubuntu 8.10 version 64bits
gnome 2.24.1
nvidia graphic card with drivers 177.80 (accélération 3D activate)

When i read a dvd movie with any player, my pc freeze randomly (on fullscreen or not). Anyone have a clue for this freeze?
My ubuntu is freshly installed.

Other problem i have encountered when i try to read an encrypted dvd (libdvdcss, libdvdnav, libdvdread installed):
- with totem it read the "intro" correctly (logo and advertisement) then a black screen. I can only see it can determine the lenght of the dvd but seems it can read it.
- with vlc, it read the chapter menu correctly but once i choose one to play, the sound/vidéo is screw up and a lot pixelized. If i type "vlc /dev/dvd" here the log:
```

libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: AVBD_91466
libdvdnav: DVD Serial Number: 365090e5
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/monnomutilisateur/.dvdnav/AVBD_91466.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fb0000. Regions: 3

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000131
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002f76
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000c43b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0035c184
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0035c188
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
libdvdnav: Language 'en' not found, using 'ja' instead
libdvdnav: Menu Languages available: ja
[00000386] main decoder error: decoder is leaking pictures, resetting the heap
```

- with xine, it read the "intro" correctly then said it can't read because the dvd is encrypted and invite me to use libdvdcss?!!
I have manage to solve the problem in the xine's setting at the CSS decryptage method by changing key to title.

Is there a way to succes reading this encrypted dvd with vlc or should i resign myself to remove both vlc and totem?

Thx for your attention

---

