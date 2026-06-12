---
title: "Problems with Handbrake"
date: 2016-10-26
forum: Multimedia Software
---

### Post by shane_faulkinbury2 on 2016-10-26
Last year I was having problems copying some of my dvd's to my computer and then to my external hdd.  My external hdd failed and now i need to copy my dvd's again.  I however cannot copy some of the newer ones now.  I have since upgraded from 15.10 to 16.10 and can no longer copy them.  I have installed libdvd-pkg and ran sudo dpkg-reconfigure libdvd-pkg.  I have also installed libdvdcss2, but still no go!  Do I have to install anything else to copy them?

---

### Post by cariboo on 2016-10-27
Clicking the Activity button should show what is happening when converting a dvd, and any errors that come up.

---

### Post by shane_faulkinbury2 on 2016-10-27
Well here is the activity after I try to record.

```
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000130
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00004581
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00007bad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003ba64c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x003ba64c)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003dc071
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x003dc071)!!
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdread: Can't seek to block 4046954
libdvdread: Can't seek to block 4046954
libdvdread: Invalid IFO for title 3 (VTS_03_0.IFO).
libdvdnav: ifoOpenVTSI failed
[10:04:53] scan: title angle(s) 1
[10:04:53] dvdnav: stop encountered during seek
[10:04:54] libhb: scan thread found 0 valid title(s)
```

---

### Post by lisati on 2016-10-27
The following tells me that you might want to check the disk for fingerprints or other such things that could hinder the ability to read the disk:
> libdvdread: Can't seek to block 4046954
libdvdread: Can't seek to block 4046954

---

### Post by mc4man on 2016-10-27
Well you also are showing errors cracking CSS keys, so inability to read some 'blocks' may be a slight red herring
(though do check disc condition..

Not sure what HB means by "block" as that's just a chunk of data. Dvd's are made up of sectors, each 2048 bytes of user data. Assuming HB means blocks as sectors that would put  block 4046954 near inner edge on 2nd layer so odd if it could read that area on first layer
(typically dual layer dvd's are read from inner to outer back to inner

If it's treating a block as more than a sector than 4046954 is well beyond the capacity of the disk.

( you could trick dvdisaster into checking for unreadable sectors on commercial DVD_VIDEO disks, just ask if inclined.

---

### Post by lisati on 2016-10-27
> **mc4man said:**
> Well you also are showing errors cracking CSS keys, so inability to read some 'blocks' may be a slight red herring
(though do check disc condition..


My thoughts exactly. :D

---

### Post by shane_faulkinbury2 on 2016-10-27
All my DVDs are as clean as they were the day I took them out of the box.  I also store them in their cases, but to make sure I wiped the back down and still no go!  I'm beginning to think it's a problem with 16.10.  It worked fine when I upgraded from 15.10 to 16.04.  Maybe I'll ask if they have a solution on the HandBrake site.

---

