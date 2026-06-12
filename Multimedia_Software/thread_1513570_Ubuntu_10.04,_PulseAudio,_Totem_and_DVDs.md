---
title: "Ubuntu 10.04, PulseAudio, Totem and DVDs"
date: 2010-06-19
forum: Multimedia Software
---

### Post by HTML-insane on 2010-06-19
So there's just one DVD (Narnia) that won't play on my Ubuntu machine using Totem: other DVDs play (I've installed libdvdread4 and libdvdcss2 like a good boy) and non-pulseaudio players like VLC play it properly. If I completely remove and kill pulseaudio, it plays in totem fine. It gets to the language selection screen and I select English, but as soon as any sound is involved it doesn't play. Clicking Go --> DVD menu causes Totem to hang.

Anybody know what the problem is? I don't want to be uninstalling pulseaudio, and VLC player is a bit complex for the mother.

The output of totem:

```
marcus@margit-laptop:~$ totem
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 43D1F9FE (GEAR):
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/marcus/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000002da
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000003e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00037447
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00331597
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0033176c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00331912
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003319c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00331e17
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00331eca
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00332a20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00332ad3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00334892
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00334945
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00334d4e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00334e01
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0035521a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003552cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0035926f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00359322
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 0
marcus@margit-laptop:~$ 
```

Note that before the last line, Totem does absolutely nothing. It just sits their. Like it's trying to devour my soul or something.

---

### Post by Yellow Pasque on 2010-06-19
Terminal output from Totem when attempting to play the DVD in question might be helpful... (or maybe not :P)

---

### Post by HTML-insane on 2010-06-19
Output added to the original post.

---

