---
title: "DVD Playback Issues in Ubuntu 8.10 (yes I installed the repositories!)"
date: 2009-06-18
forum: Multimedia Software
---

### Post by dbsoundman on 2009-06-18
I'm having some aggrivating issues with DVD playback in one of my Ubuntu machines. I tried watching season 6 of Family Guy on DVD tonight, but I could not get the DVD to play, using two different programs. I first tried Totem, which showed the WARNING and Fox logo screens at a really really slow frame rate; less than 1 frame per second it seemed. I never got to the main menu with Totem. So, I tried xine. Xine got through the WARNING and Fox logo screens just fine, but then failed with a DVD read error when it got to the main menu. It even played the little commercial that comes before the menu with no problems. Anyone have an idea of what might be going on here? It's really irritating.

Thanks,
Dan

---

### Post by dbsoundman on 2009-06-19
Someone has to have an idea here! I don't recall having this issue before, but I can't get DVDs to play on either of my computers! I can RIP DVDs just fine, I just can't PLAY them. It's not like these computers are similar, either: this one is an AMD 64 Athlon X2, the other is an old dual-processor Pentium III. Help!

-Dan

---

### Post by dbsoundman on 2009-06-21
OK, I tried a few things tonight. I noted that some dvds require libdvdcss2 to run, but I already had that installed on both computers! I installed gxine (I had been trying totem and xine before), and here's the terminal output:
```
dan@blackdiamond:~$ gxine
bind: No such file or directory
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/dan/.xine/cddbcache
warning: configuration item media.capture.save_dir points to a non-existent location 
warning: configuration item media.dvb.channels_conf points to a non-existent location /home/dan/.xine/channels.conf
warning: configuration item media.dvd.raw_device points to a non-existent location /dev/rdvd
warning: configuration item media.video4linux.radio_device points to a non-existent location /dev/radio0
warning: configuration item media.video4linux.video_device points to a non-existent location /dev/video0
warning: configuration item media.wintv_pvr.device points to a non-existent location /dev/video0
warning: configuration item decoder.external.real_codecs_path points to a non-existent location 
warning: configuration item subtitles.separate.font_freetype points to a non-existent location 
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
libdvdnav: Using dvdnav version 1.1.15 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: SYNECDOCHE_NEW_YORK
libdvdnav: DVD Serial Number: 3a42be33
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/dan/.dvdnav/SYNECDOCHE_NEW_YORK.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000179
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000025d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000318
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000402
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000004bd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00099afb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00099bb6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00099c93
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00099d4e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00099e4f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000a2648
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0029a4bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0029a58b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0029a679
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0029a734
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0029b800
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0029b8bb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0029b99a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0029ba55
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0029cc25
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0029cce0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x0029cfed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0029d0a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x0029d189
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0029d244
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x002c9e80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x002c9f3b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x002dbb51
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x002dbc0c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x002dbcef
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x002dbdaa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x00325415
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003254d0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x003b28f6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003b29b1
libdvdread: Elapsed time 0
libdvdread: Found 17 VTS's
libdvdread: Elapsed time 0
open_wv_file: non-seekable inputs aren't supported yet.
xine-lib: error: Read error from:: Error reading NAV packet.

```

So it can't read the NAV packet...isn't that what libdvdcss is supposed to help with? What's the problem here?

-Dan

---

### Post by dilb on 2009-08-03
Did you ever resolve this? I had the same problem with gxine (NAV packet issue). I found installing the restricted extras - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) - resolved the problem.

---

