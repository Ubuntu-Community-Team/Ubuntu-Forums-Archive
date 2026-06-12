---
title: "Problem playing DVD's"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by MilkeySUFC on 2008-01-24
I have a problem playing commercial DVD's. 

After a clean install of Ubuntu & updates, I followed the MEDIBUNTU instructions to load codecs, CSS2 and what not. Problem is commercial DVD's will not play.

I installed Totem-xine as some have suggested but still no DVD playback, either when inserting DVD & autoplaying or loading Totem & clicking File->Play "DVDNAME".

What do I check to confirm correct installation? 

TIA.

---

### Post by eye208 on 2008-01-24
Start Totem from a terminal window so you can see the error messages. Also try MPlayer and VLC; they provide lots of info.

---

### Post by MilkeySUFC on 2008-01-24
> **eye208 said:**
> Start Totem from a terminal window so you can see the error messages. Also try MPlayer and VLC; they provide lots of info.

This is the output from starting Totem in a terminal:
libdvdnav: Using dvdnav version 1.1.7 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdd mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/mike/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00063df5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0006418a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00066ca7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00067d95
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0006a4f5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0006a52e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00087fad
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0

MPlayer & VLC both play the DVD's.

Still would like to get to the bottom of what's wrong for Totem.

Any help much appreciated.

Thanks, Milkey

---

