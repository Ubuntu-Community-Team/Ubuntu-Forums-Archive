---
title: "Encrypted Dvd's (any media player)"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by gRoberts on 2006-10-29
Hi all,

It's a quiet day and I decided to stick a few dvd's on whilst i cure a night of drinking.

Got through my first DVD, but then came to the second and received an error stating that I'm trying to watch an encrypted dvd without libdvdcss.

I have libdvdcss2 installed plus I have automatix2 etc, but none seem to work, alas I do get mplayer to play the first part of the dvd which is scrambled on screen and then it closes.

when trying to use Totem, I had this in the console.

Any idea's?

Gav

```

gavin@EYCD:~$ totem
totem: /home/gavin/mono-1.1.18/lib/libpng12.so.0: no version information availab le (required by /usr/lib/libcairo.so.2)
libdvdnav: Using dvdnav version 1.1.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS a uthentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/gavin/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000139
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001a6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000001be
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000001be)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000da3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000ae3e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0000cb82
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0000cbd9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001ecde2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001ece39
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001f44c8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001f451f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00218cdf
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x00218cdf)
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00218d36
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00219b14
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00219b6b
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 2
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
libdvdnav: Using dvdnav version 1.1.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS a uthentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/gavin/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000139
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001a6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000001be
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000001be)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000da3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000ae3e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0000cb82
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0000cbd9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001ecde2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001ece39
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001f44c8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001f451f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00218cdf
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x00218cdf)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00218d36
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00219b14
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00219b6b
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 2
gavin@EYCD:~$

```

---

