---
title: "Store bought (encrypted) DVD playback in Ubuntu 8.04?"
date: 2008-08-17
forum: Multimedia Software
---

### Post by michaelfougnie on 2008-08-17
How do I get Ubuntu 8.04 to play DVDs?

---

### Post by lisati on 2008-08-17
Chances are you'll have to install some "extras". Have a look here: [https://help.ubuntu.com/8.04/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/8.04/musicvideophotos/C/video.html#video-dvd)

---

### Post by WRDN on 2008-08-17
Run:

```
sudo apt-get install ubuntu-restricted-extras
```

Now, run:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by FJGamer on 2008-08-17
Do what WRDN says. You have to use the terminal to install the needed libraries/whatever to watch your DVDs. Just go to "Applications" on the top menu bar, in the upper left corner of the screen. Then, go to "Accessories" and load "Terminal." After that, type what WRDN mentioned:

```
sudo apt-get install ubuntu-restricted-extras
```
Press ENTER/RETURN and type in your password if it asks... and press ENTER/RETURN again. (Password does not show up. Don't worry.)
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
Type that. Press the ENTER/RETURN key and it will probably ask for a password again. Afterwards, close out of the terminal window and try playing a DVD in either Totem or VLC.

---

### Post by cooke77 on 2008-08-17
Try either the KLC Media Player or Ogle, in Kubuntu 8.04.
Ogle is very basic but it works.
So does the KLC.
Just open it up, and select 'DVD' tab. 
It gives a variety of media types...to play, just select DVD...and, you're away.

---

### Post by iamcims on 2008-08-26
ive tried both of those things, plus many other tricks online, my vlc still closes and other players say its encrypted.

```

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/tim/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0006d250
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0006d2ec
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x0006d2ec)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00078c96
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00078c96)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00330750
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003a66b3
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x003a66b3)!!
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 1
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
*** Zero check failed in ifo_read.c:1604
    for pgcit->zero_1 = 0xd3b7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1608 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***

*** Zero check failed in ifo_read.c:648
    for pgc->zero_1 = 0xc8d3

*** libdvdread: CHECK_VALUE failed in ifo_read.c:649 ***
*** for pgc->nr_of_programs <= pgc->nr_of_cells ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:668 ***
*** for pgc->cell_playback_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:669 ***
*** for pgc->cell_position_offset != 0 ***

libdvdnav: ifoRead_PGCIT failed - CRASHING!!!
vlc: vm.c:206: ifoOpenNewVTSI: Assertion `0' failed.
Aborted
```

---

### Post by eye208 on 2008-08-26
Is your DVD drive new? Maybe its region has not yet been set. DVD playback is impossible on drives with unset region. The same thing happened to me last year. The "regionset" tool can display and optionally set the region of the drive.

[http://packages.ubuntu.com/hardy/regionset](http://packages.ubuntu.com/hardy/regionset)

> Regionset is a small utility which displays and sets the region/zone setting of a DVD drive, allowing it to decrypt the DVD's sold in this geographical zone. **Hardware vendors often limit the number of such modifications, but it is necessary to set it at least once with a brand new drive**.

---

