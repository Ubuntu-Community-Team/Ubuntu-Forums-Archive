---
title: "DVD Encryption?"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by lucia on 2007-04-15
Hi everyone!

I've bought a movie dvd but it won't play in any of my Ubuntu dvd players, as well as in most of my windows dvd players. It's not broken though, it works fine in one (commercial) dvd player in windows.

I've installed libdvdcss, and I've never had problems with watching other dvds.
Is this some new method of encryption, or is something wrong with the software? :confused: 

In xine v0.99.4, I get the following output:
> libdvdnav: Using dvdnav version 1.1.2 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: WER_FRUEHER_STIRBT_IST_LAENGER! 
libdvdnav: DVD Serial Number: 364172a7
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/lucia/.dvdnav/WER_FRUEHER_STIRBT_IST_LAENGER!.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000025d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000025f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000294f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000330ec
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0004bd49
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002a253f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002a272f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002b4514
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002b4541
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002bd152
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002bdc0f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00374155
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 1

*** libdvdread: CHECK_VALUE failed in ifo_read.c:435 ***
*** for vtsi_mat->vtsi_last_sector*2 <= vtsi_mat->vts_last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:439 ***
*** for vtsi_mat->vtsm_vobs == 0 || (vtsi_mat->vtsm_vobs > vtsi_mat->vtsi_last_sector && vtsi_mat->vtsm_vobs < vtsi_mat->vts_last_sector) ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:442 ***
*** for vtsi_mat->vtstt_vobs == 0 || (vtsi_mat->vtstt_vobs > vtsi_mat->vtsi_last_sector && vtsi_mat->vtstt_vobs < vtsi_mat->vts_last_sector) ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed
xine-lib: Fehler: Read error from::  Encrypted or faulty DVD
Xlib: unexpected async reply (sequence 0x30d9)!


I hope someone can help me here!
lucia :popcorn:

---

### Post by metnik on 2007-04-16
did u follow [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) ?

---

### Post by lucia on 2007-04-17
Yes, I did, and it works with every other DVD except this one ... :(

---

### Post by Oxygene on 2007-04-17
I've the same problem. Programs like DVD shrink or DVD decrypter on windows also crash. Seems like "they" found a way to make a lot of free programs unusable :(

---

### Post by Oxygene on 2007-04-17
funny enough, I just see that it seems to be the same DVD title that causes the problem...

---

### Post by Oxygene on 2007-05-05
For those of you who speak german, it's a new kind of copy protection:
[http://www.heise.de/newsticker/meldung/89306](http://www.heise.de/newsticker/meldung/89306)

---

### Post by RawMustard on 2007-05-05
You'll probably need to decrypt it using DVDFab, it's a windows program unfortunately.
It's the only thing I've found that will look at DVD's with this new fair use screwing copy protection.  Anyway, I've heard people have got it working under wine!

---

### Post by RobbieCrash on 2007-05-09
I tried playing a dvd on Ubuntu with VLC, and no dice, but playing it on Windows with VLC and no additional dvd software or decoder installed, and it runs fine.

Any new ideas?

---

