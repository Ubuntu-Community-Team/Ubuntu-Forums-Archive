---
title: "Audio CDs not detected in 9.10"
date: 2010-01-16
forum: Multimedia Software
---

### Post by isantop on 2010-01-16
If I put an Audio CD in my CD-ROM drive, then try to open Sound Juicer, I get an error saying that Sound Juicer cannot find any CD-ROM Drives to read. I can't rip my audio cd.

Similar attempts in K3b yielded similar results, albeit differently worded error messages.

---

### Post by dowell_p on 2010-01-16
I am a novice with Ubuntu. I have been using it for a couple of years and this is my first real problem. I upgraded from Intrepid to Karmic through the update manager and I have the same issue. I found this thread 

[http://ubuntuforums.org/showthread.php?t=767836&page=2]("http://ubuntuforums.org/showthread.php?t=767836&page=2")

and installed the libcdio-utils, per the final thread, but it did not work. 

I think the above thread is on the right track, because if I pop in a data CD it starts properly and I can browse the disk just fine.

When I go to nautilus and try to open the cdrom, I get this error.

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so  

So I go to terminal and try dmesg | tail and get 

[ 1084.200218] UDF-fs: No anchor found
[ 1084.200223] UDF-fs: No partition found (1)
[ 1084.249543] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1084.249555] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1084.249564] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 1084.249578] end_request: I/O error, dev sr0, sector 64
[ 1084.249689] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 1251.066855] UDF-fs: No VRS found
[ 1251.066867] UDF-fs: No partition found (1)
[ 1251.105014] ISO 9660 Extensions: RRIP_1991A

I have no clue what any of this means, but my guess is just that it can read the cdda format and therefore cant mount the cdrom.

I hope this can be of help.

---

### Post by lyall on 2010-01-18
> **isantop said:**
> If I put an Audio CD in my CD-ROM drive, then try to open Sound Juicer, I get an error saying that Sound Juicer cannot find any CD-ROM Drives to read. I can't rip my audio cd.

Similar attempts in K3b yielded similar results, albeit differently worded error messages.

see the following link 
[http://ubuntuguide.org/wiki/Ubuntu:Karmic]("http://ubuntuguide.org/wiki/Ubuntu:Karmic")
scroll down to ***9 Software Troubleshooting***

see if that helps

bookmark the link to ubuntu guides if might help you later, with this problem
or some other problem that you might have

good luck and have fun learning

---

### Post by isantop on 2010-01-22
I tried reading through the guide, but I found nothing for my problem, so I'm guessing it is somewhat complex. No help yet.:(

---

### Post by gravyboat on 2010-03-06
I'm having the same issue.

"No CD-ROM drives found

Sound Juicer could not find any CD-ROM drives to read."

---

