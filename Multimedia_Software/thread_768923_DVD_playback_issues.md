---
title: "DVD playback issues"
date: 2008-04-26
forum: Multimedia Software
---

### Post by mrzack on 2008-04-26
I just bought The Clash Live: Revolution Rock DVD, and I can't seem to get it to play on Heron. I installed the Gstreamer codecs, libdvdcss2, and w32codecs. I can play older DVDs, but this one doesn't even appear when put in the drive.

---

### Post by mc4man on 2008-04-26
> but this one doesn't even appear when put in the drive.
Is it mounting, ie. showing up on desktop as icon

---

### Post by hutxubix on 2008-04-26
I have just installed xubuntu hardy and it doesn't play DVDs either. Bug perhaps?

---

### Post by bodam on 2008-04-26
I'm having the same issue.  I just got a brand new Serval and, of course, the first thing I did was reimage with 8.04 LTS Gold (64 bit) and I cannot get the DVD playback working with commercial DVDs (I've tried 2 so far) but homemade dvds work just fine.  I have installed libdvdcss and libplayback3 (name may be wrong) I also tried installing totem-xine and VLC but none of them seem to work.  Here's the output I get from Totem-xine if I kick it off from a command line and play an encrypted DVD: 

bodam@bodam-laptop:~$ totem-xine
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/bodam/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000198
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000198)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00001926
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0020087f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002008b8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002022b2
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002022eb
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 2
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1526 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1526 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/bodam/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000198
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000198)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00001926
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0020087f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002008b8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002022b2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002022eb
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.


any ideas??

---

### Post by mc4man on 2008-04-26
> brand new Serval what does this mean
Have you ever played commercial dvds on this box ?

---

### Post by ubuntu-freak on 2008-04-26
Some new DVDs have a higher encryption, try no.9 in the troubleshooting section of my [how-to](http://ubuntuforums.org/showthread.php?t=766683).
 
Nathan

---

### Post by mrzack on 2008-04-28
> **reassuringlyoffensive said:**
> Some new DVDs have a higher encryption, try no.9 in the troubleshooting section of my [how-to](http://ubuntuforums.org/showthread.php?t=766683).
 
Nathan

How do I apply the patch that is mentioned in no. 9?

---

### Post by ubuntu-freak on 2008-04-28
> **mrzack said:**
> How do I apply the patch that is mentioned in no. 9?

 
It's mentioned in the link no? 
 
Nathan

---

### Post by mc4man on 2008-04-28
@mrzack
If not clear I did a little re explaining for someone here [http://ubuntuforums.org/showthread.php?p=4816539#post4816539](http://ubuntuforums.org/showthread.php?p=4816539#post4816539)

---

### Post by mrzack on 2008-04-29
> **reassuringlyoffensive said:**
> It's mentioned in the link no? 
 
Nathan

I overlooked it somehow. And a huge thanks to everyone who helped. All of my newer DVDs play now.

---

