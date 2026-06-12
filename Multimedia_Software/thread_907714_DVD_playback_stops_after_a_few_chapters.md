---
title: "DVD playback stops after a few chapters"
date: 2008-09-01
forum: Multimedia Software
---

### Post by han555 on 2008-09-01
I am trying to play a DVD in VLC (although I get the same problem on all players I've tried; just different error messages) and playback stops after a few chapters in.  This doesn't happen with all DVDs I try however.  Some play all the way through just fine.  I've already followed all of the typical instructions out there.  I have all of the libraries installed (libdvdcss, libdvdnav, libdvdread) and I have set the region to region 1 using regionset.  The same problem happens with region0 and region1 dvds.  The output from VLC is below.  It crashes when I attempt to skip ahead to chapter 10 (Can't seek to block 777472). This happens at different chapters depending on the DVD.  What I've noticed is that the disc itself contains more .VOB files than are found below.  I'm not sure if that's a problem or not.

```

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DEATHRACE
libdvdnav: DVD Serial Number: 258f1cd6
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/h/.dvdnav/DEATHRACE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000153
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000dcc8
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
[00000310] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
libdvdread: Can't seek to block 777472
[00000289] main playlist: nothing to play

```

Here's the output from totem:
```

libdvdnav: Using dvdnav version 1.1.11.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/brettm/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
libdvdnav: Using dvdnav version 1.1.11.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/brettm/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

```

When I try to change chapters in totem it gives me the error, "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"  But, as I've said, I do have libdvdcss installed.

Any thoughts?

---

### Post by mc4man on 2008-09-01
The one obvious possibility is your dvd drive can't or is having trouble reading layer1.

While not definitive (due to varying quality of dvd stamping and or physical damage) I'd compare sizes of titles that play thru vs. those that don't.

If the majority of those that play are 4.7Gb or less (single layer) and those that fail greater than 4.7Gb (dual layer) i'd put blame on the drive.

Note that physical damage to disks also would be a potential factor

---

