---
title: "DVD help"
date: 2009-12-03
forum: Multimedia Software
---

### Post by robert_edgar on 2009-12-03
Hi everyone,

I've managed to get ubuntu 9.10 working quite nicely except i cannot get DVDs to play.

Tried to open in vlc but got errors, after some searching installed libdvdcss2 but still getting errors.
Here is the output when I run
```
cvlc -v dvd://
``````
VLC media player 1.0.2 Goldeneye
[0x26f7668] main demux warning: no access_demux module matching "file" could be loaded
[0x270ece8] main interface error: no interface module matched "globalhotkeys,none"
[0x270ece8] main interface error: no suitable interface module
[0x25f7888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x270ecb8] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: TRANSFORMERS_PAL
libdvdnav: DVD Serial Number: 37328942
libdvdnav: DVD Title (Alternative): TRANSFORMERS_PAL
libdvdnav: Unable to find map file '/home/robert/.dvdnav/TRANSFORMERS_PAL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0001f984
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001ff4f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0001fff0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00024abd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0002a8d4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0002d02e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0002d06d
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x0002d06d)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0003b8de
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00387760
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
[0x27120b8] dvdnav demux error: cannot set title (can't decrypt DVD?)
[0x27120b8] main demux error: Playback failure
[0x27120b8] main demux error: VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Invalid title IFO (VTS_04_0.IFO).
[0x27120b8] dvdread demux error: fatal error in vts ifo
[0x27120b8] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[0x27120b8] main demux warning: no access_demux module matching "dvd" could be loaded
[0x27241b8] main access error: no access module matched "dvd"
[0x2713738] main input error: open of `dvd://' failed: no access module matched "dvd"
[0x2713738] main input error: Your input can't be opened
[0x2713738] main input error: VLC is unable to open the MRL 'dvd://'. Check the log for details.


```Any help is greatly appreciated

Cheers, Robert

---

### Post by gnat79 on 2009-12-03
I had a similar problem with 9.04. I installed all the software, including libdvdcss2, as outlined in the guide. However, I NEVER got libdvdcss2 working. I had no problems when I upgraded to Karmic. I always thought that there was an issue with decryption, but reinstalling all the packages, uninstalling and then reinstalling, etc, never worked.

---

### Post by robert_edgar on 2009-12-05
Can anyone suggest anything here?
Don't want to install windows just so i can get dvds to play!!

Cheers

---

### Post by xc3RnbFO8P on 2009-12-05
Try to reinstall the codecs (Karmic Koala):
> sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
> sudo apt-get install libdvdcss2
> sudo apt-get install w32codecs
> sudo apt-get install libdvdread4
> sudo /usr/share/doc/libdvdread4/install-css.sh
and restart the computer.

---

### Post by robert_edgar on 2009-12-06
Thanks a lot Ringi that worked!:P 

now all i need is :popcorn:

---

