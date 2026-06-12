---
title: "DVD source plug-in? HELP!"
date: 2009-07-13
forum: Multimedia Software
---

### Post by spankster32808 on 2009-07-13
[SIZE=3]Hi All:

     I am running a Gateway Solo 1450 notebook computer with Ubuntu 9.0.4 Jaunty Jackalope.  I am trying to play a DVD on my laptop, but when Movie Player opens, it says that I need a plug-in for DVD Source.  Whenever I tell the computer to search for one, it returns no results.  I am complete and total newbie to Ubuntu :razz: and need some idiot-proof instructions on how to fix this!  ](*,) Thanks in advance for any help you may be able to provide![/SIZE]

---

### Post by starcraft.man on 2009-07-13
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Read applicable sections. Almost certain you simply need the dvdcss2.

Also, be sure to install the restricted extras package, open a terminal (Applications > Accessories > Terminal) then type and enter:
```

sudo apt-get install ubuntu-restricted-extras

```

Then you put in password and it will install a lot of extras most people need, including java, flash, codecs for video and some other things. If you want to understand the command (this or medibuntu) please see my guide in sig on installing.

---

### Post by hmancha on 2011-02-18
Was having same problem. Applied suggested downloads. They worked!!!!!! 
Thanx :P

---

### Post by phosphide on 2011-02-19
Hi all,

I am running into a problem and I have downloaded just about every codec/terminal command there is.

Here is the terminal output when I attempt to play a dvd from vlc.

```
VLC media player 1.0.6 Goldeneye
[0xb5e4b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: AVATAR
libdvdnav: DVD Serial Number: 3C63A5C7
libdvdnav: DVD Title (Alternative): AVATAR
libdvdnav: Unable to find map file '/home/tristan/.dvdnav/AVATAR.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000144
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000030f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004d3
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000004d3)!!
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00001f7c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00002122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0000313e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00003302
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00005e74
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00006038
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00006246
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0002cc2f
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x0002cc2f)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003d7455
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 5
[0x7f9490002318] main input error: ES_OUT_RESET_PCR called
[0x7f9490002318] main input error: ES_OUT_RESET_PCR called
[0x7f9490002318] main input error: ES_OUT_RESET_PCR called
[0x7f9490002318] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
```

I am on 10.04 and I cannot get dvd's to work.

---

