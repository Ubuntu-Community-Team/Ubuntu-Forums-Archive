---
title: "Upgraded to 9.10 now ogmrip fails"
date: 2010-01-27
forum: Multimedia Software
---

### Post by codejammer on 2010-01-27
I recently upgraded an HP laptop and desktop machine to Ubuntu 9.10.  Previously I had ogmrip working fine in 8.10 apart from the occasional A/V sync problem caused by memcoder which was slated to be fixed in 9.10 hence the upgrade.  However now I cannot get ogmrip running at all.  If I try to rip directly from the DVD it gets about 3% done and then hangs. If I copy the ISO to the hard drive it gets to the merging operation and then hangs for several hours and finally fails with an "unknown error" message.  I've looked in the log files but can't get any useful information from there.  What can I do to get either more information to help debug the issue or hopefully fix it :)

BTW I've also tried DVDrip with similar results.

---

### Post by VertexPusher on 2010-01-27
Try copying the DVD to your hard drive using "vobcopy -m". If that fails too, it's most likely some decryption issue, probably caused by old decryption keys in the cache. In that case delete the ~/.dvdcss folder and try again.

---

### Post by codejammer on 2010-01-27
I installed vobcopy and it locked up too as soon as it got to the first large VOB file.  It got to 16% where it hung for about 10 minutes and then I killed it.  Any ideas?

andy@helen-laptop:~$ vobcopy -m
Vobcopy 1.1.0 - GPL Copyright (c) 2001 - 2007 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

[Info] Path to dvd: /dev/sr0
libdvdread: Using libdvdcss version 1.2.10 for DVD access
[Info] Name of the dvd: TERMINATOR_SALVATION
*** Zero check failed in ifo_read.c:520
    for vmgi_mat->zero_6 = 0x0000000f00000000000000000000000000000000000000000000000000000000
[Info] There are 18 titles on this DVD.
[Info] There are 183 chapters on the dvd.
[Info] Most chapters has title 13 with 53 chapters.
[Info] All titles:
[Info] Title 1 has 28 chapters.
[Info] Title 2 has 2 chapters.
[Info] Title 3 has 2 chapters.
[Info] Title 4 has 2 chapters.
[Info] Title 5 has 2 chapters.
[Info] Title 6 has 2 chapters.
[Info] Title 7 has 1 chapter.
[Info] Title 8 has 1 chapter.
[Info] Title 9 has 1 chapter.
[Info] Title 10 has 1 chapter.
[Info] Title 11 has 1 chapter.
[Info] Title 12 has 1 chapter.
[Info] Title 13 has 53 chapters.
[Info] Title 14 has 1 chapter.
[Info] Title 15 has 1 chapter.
[Info] Title 16 has 28 chapters.
[Info] Title 17 has 28 chapters.
[Info] Title 18 has 28 chapters.

[Info] There are 18 angles on this dvd.
[Info] All titles:
[Info] Title 1 has 1 angle.
[Info] Title 2 has 1 angle.
[Info] Title 3 has 1 angle.
[Info] Title 4 has 1 angle.
[Info] Title 5 has 1 angle.
[Info] Title 6 has 1 angle.
[Info] Title 7 has 1 angle.
[Info] Title 8 has 1 angle.
[Info] Title 9 has 1 angle.
[Info] Title 10 has 1 angle.
[Info] Title 11 has 1 angle.
[Info] Title 12 has 1 angle.
[Info] Title 13 has 1 angle.
[Info] Title 14 has 1 angle.
[Info] Title 15 has 1 angle.
[Info] Title 16 has 1 angle.
[Info] Title 17 has 1 angle.
[Info] Title 18 has 1 angle.

[Info] DVD-name: TERMINATOR_SALVATION
[Info]  Disk free: 47273 MB
[Info]  Vobs size: 8086 MB
[Info] Writing files to this dir: /home/andy/TERMINATOR_SALVATION/VIDEO_TS/
[Info] 
Writing to /home/andy/TERMINATOR_SALVATION/VIDEO_TS/VIDEO_TS.IFO 
  32kB of   32kB written
[Info] 
Writing to /home/andy/TERMINATOR_SALVATION/VIDEO_TS/VIDEO_TS.VOB 

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001b0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0003e7ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00057e19
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0034d894
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0034d8e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00358b99
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00358be6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003641fc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00364249
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0036b436
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0036b483
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00375045
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00375092
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00376464
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003764b1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003773b6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00377403
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x00377c50
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00377c9d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00377e52
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x00377eb0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x00377f0d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x0037806a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003aa00f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003cf5ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003cf600
libdvdread: Elapsed time 0
libdvdread: Found 15 VTS's
libdvdread: Elapsed time 0
   0MB of    0MB written ( 100.0% ) 
[Info] 
Writing to /home/andy/TERMINATOR_SALVATION/VIDEO_TS/VIDEO_TS.BUP 
  32kB of   32kB written
[Info] 
Writing to /home/andy/TERMINATOR_SALVATION/VIDEO_TS/VTS_01_0.IFO 
 120kB of  120kB written
[Info] 
Writing to /home/andy/TERMINATOR_SALVATION/VIDEO_TS/VTS_01_0.VOB 
 203MB of  203MB written ( 100.0% ) 
[Info] 
Writing to /home/andy/TERMINATOR_SALVATION/VIDEO_TS/VTS_01_1.VOB 
^C^CMB of 1024MB written ( 1.6 % )

---

### Post by codejammer on 2010-01-28
After a search on the web I found dvdisaster which reportedly can extract DVD images from DVDs with bad sectors caused by scratches etc.  Although the disk I have is in perfect condition I thought I'd give it a go.  It ran overnight and seems to have extracted the ISO image from the disk, the GUI has an indicator that shows the bad sectors that could not be read and indeed there is a bad section a short way in from the start at the centre of the disk.  OMGrip could open the archive so I have left it ripping the main title at the moment.  I'll let you know if it's successful later.

---

### Post by codejammer on 2010-01-28
Hmmmm.... that didn't work either.  I tried playing it with mplayer and vlc and neither would touch it so I went back to vobcopy and tried to copy just the specific title that I wanted...  Now this gives the following...

```
andy@helen-laptop:~/TerminatorSalvation$ vobcopy -n 1 -l
Vobcopy 1.1.0 - GPL Copyright (c) 2001 - 2007 robos@muon.de
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

[Info] Path to dvd: /dev/sr0
libdvdread: Using libdvdcss version 1.2.10 for DVD access
[Info] Name of the dvd: TERMINATOR_SALVATION
*** Zero check failed in ifo_read.c:520
    for vmgi_mat->zero_6 = 0x0000000f00000000000000000000000000000000000000000000000000000000
[Info] There are 18 titles on this DVD.
[Info] There are 183 chapters on the dvd.
[Info] Most chapters has title 13 with 53 chapters.

[Info] There are 18 angles on this dvd.
[Info] Using Title: 1
[Info] Title has 28 chapters and 1 angles
[Info] Using Chapter: 1
[Info] Using Angle: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001b0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0003e7ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00057e19
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0034d894
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0034d8e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00358b99
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00358be6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003641fc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00364249
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0036b436
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0036b483
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00375045
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00375092
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00376464
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003764b1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003773b6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00377403
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x00377c50
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00377c9d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00377e52
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x00377eb0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x00377f0d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x0037806a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003aa00f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003cf5ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003cf600
libdvdread: Elapsed time 0
libdvdread: Found 15 VTS's
libdvdread: Elapsed time 0

[Info] DVD-name: TERMINATOR_SALVATION

[Info] Outputting to /home/andy/TerminatorSalvation/TERMINATOR_SALVATION1.vob
  16MB of 6061MB written (0 %)
[Error] Write() error
[Error] It's possible that you try to write files
[Error] greater than 2GB to filesystem which
[Error] doesn't support it? (try without -l)
[Error] Error: Bad address

```

Event though I didn't use the -l switch it seems to think I did... not sure why...  Any help appreciated.

---

### Post by codejammer on 2010-02-18
In the end I decided to try Handbrake and it seems to work well.  It successfully rips these DVDs and the AV sync problems that I had with other DVDs don't seem to exist any more :).

---

### Post by ghostborg on 2010-02-22
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Don't forget to follow the directions on Medibuntu after upgrading or installing to make sure everything is in place to decrypt a dvd.

K9copy and DVDFabfree-(Wine) work pretty good for ripping DVD's.

Best to rip to hard disc first then encode from hard disc.

---

