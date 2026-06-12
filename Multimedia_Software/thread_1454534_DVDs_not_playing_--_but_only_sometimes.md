---
title: "DVDs not playing -- but only sometimes"
date: 2010-04-14
forum: Multimedia Software
---

### Post by pseudocube on 2010-04-14
My newly installed (but not new) DVD drive seems to play some movies some days, but others all the time. I'm pretty sure it's just a little picky about scratches. I can hear it in the drive; when I insert the disk, I can tell when it isn't spinning. When it does start spinning, that's when the Media options window pops up asking me what I want to do with the disk.

Here's the error message I get in VLC 1.0.5 on Ubuntu Lucid Lynx beta:

```
user@desktop-computer:~$ vlc dvd://
VLC media player 1.0.5 Goldeneye
[0x9b85668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0x9e98888] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0x9e98888] main access error: no access module matched "dvd"
[0x9c346e8] main input error: open of `dvd://' failed: no access module matched "dvd"

```

I know this is most likely a hardware problem, but if there's any way to get the DVD to mount every time, that would be nice.

---

### Post by pseudocube on 2010-04-16
50 views, no replies? :( Don't be shy!

---

### Post by pseudocube on 2010-05-14
My problem still persists, but I have determined that it has nothing to do with how scratched the DVD is.

---

### Post by jacrider on 2010-05-15
Do some more searching, there appears to be an issue with 10.04 and mounting of optical disks.  

I have gone back to 9.10 so I can read DVD's and CD's.

Hopefully this will be resolved soon.

---

### Post by smuggly on 2010-05-15
Have You Tried Mounting the dvd drive manually? I know this is a hassel but it might work if u really need it.

---

### Post by pseudocube on 2010-05-17
> **jacrider said:**
> Do some more searching, there appears to be an issue with 10.04 and mounting of optical disks.  

I have gone back to 9.10 so I can read DVD's and CD's.

Hopefully this will be resolved soon.

Thank you. As Internet connectivity is somewhat of a hassle to get on this computer (it's on the other end of the house from the router with no wifi support) I can only update every so often. How will I know when the fix is out, so I can update then? 

> **smuggly said:**
> Have You Tried Mounting the dvd drive manually? I know this is a hassel but it might work if u really need it.

How might I do that? The DVD doesn't show up under "computer", does it need to do that in order to mount it, or does mounting it allow it to show up under "computer" and thus allow me to play the files?

---

### Post by pseudocube on 2010-05-31
I solved my problem (I think). I inserted a laser cleaner disk, and my DVDs don't seem to be having trouble anymore.

---

### Post by pseudocube on 2010-08-03
Aaarg! It's definitely not a dirty lens.

```
andrew@andrew-desktop:~$ vlc dvd://
VLC media player 1.0.6 Goldeneye
[0x8203668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title:  
libdvdnav: DVD Serial Number: 34FACBD7
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/andrew/.dvdnav/ .map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000149
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000aa4e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000aaec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0008e749
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000cc8a4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0015996d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001abcd4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001d441c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x001e44be
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x001e7c59
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x001eb748
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x001ee0ed
libdvdread: Elapsed time 0
libdvdread: Found 10 VTS's
libdvdread: Elapsed time 0
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_13_0.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_13_0.BUP failed
libdvdread: Can't open file VTS_13_0.IFO.
libdvdnav: ifoOpenVTSI failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_13_0.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_13_0.BUP failed
libdvdread: Can't open file VTS_13_0.IFO.
libdvdnav: ifoOpenVTSI failed
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
^C[0x82038a8] signals interface error: Caught Interrupt signal, exiting...
andrew@andrew-desktop:~$ vlc dvd://
VLC media player 1.0.6 Goldeneye
[0x8d5b668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title:  
libdvdnav: DVD Serial Number: 34FACBD7
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/andrew/.dvdnav/ .map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000149
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000aa4e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000aaec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0008e749
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000cc8a4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0015996d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001abcd4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001d441c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x001e44be
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x001e7c59
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x001eb748
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x001ee0ed
libdvdread: Elapsed time 0
libdvdread: Found 10 VTS's
libdvdread: Elapsed time 0
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_13_0.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_13_0.BUP failed
libdvdread: Can't open file VTS_13_0.IFO.
libdvdnav: ifoOpenVTSI failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_13_0.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_13_0.BUP failed
libdvdread: Can't open file VTS_13_0.IFO.
libdvdnav: ifoOpenVTSI failed
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.


```

---

