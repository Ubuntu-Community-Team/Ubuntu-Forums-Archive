---
title: "Can watch, but not rip DVDs - CRC Errors"
date: 2010-10-30
forum: Multimedia Software
---

### Post by wetmonkey on 2010-10-30
Hello 
I recently purchased a netbook which does not have a DVD drive.  I have attempted to rip a copy of some DVDs I own to facilitate watching them on the netbook.  I have run into some errors. 

First the setup:
Ubuntu 10.04 LTS
Linux ub-desktop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux
DVD Drive - HL-DT-ST DVDRRW GSA-4166B 

I have tried multiple DVDs (Heat, Team America, The Messenger, Holy Grail).  All fail in the same way. 

I can watch any of these DVDs from start to finish in VLC or mPlayer.  No issues there. 

For ripping I tried AcidRip, DVD::RIP, and even fired up a virtual box of Windows to try different applications.    

The error log shows:

```

Oct 30 20:39:51 ub-desktop kernel: [35005.981805] sr 4:0:0:0: [sr0] Unhandled sense code
Oct 30 20:39:51 ub-desktop kernel: [35005.981814] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 30 20:39:51 ub-desktop kernel: [35005.981822] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
Oct 30 20:39:51 ub-desktop kernel: [35005.981831] sr 4:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
Oct 30 20:39:51 ub-desktop kernel: [35005.981841] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 1f 87 c2 00 00 3f 00
Oct 30 20:39:51 ub-desktop kernel: [35005.981857] end_request: I/O error, dev sr0, sector 8265480
Oct 30 20:39:51 ub-desktop kernel: [35005.981867] __ratelimit: 53 callbacks suppressed
Oct 30 20:39:51 ub-desktop kernel: [35005.981873] Buffer I/O error on device sr0, logical block 2066370
Oct 30 20:39:51 ub-desktop kernel: [35005.981884] Buffer I/O error on device sr0, logical block 2066371
Oct 30 20:39:51 ub-desktop kernel: [35005.981897] Buffer I/O error on device sr0, logical block 2066372
Oct 30 20:39:51 ub-desktop kernel: [35005.981903] Buffer I/O error on device sr0, logical block 2066373
Oct 30 20:39:51 ub-desktop kernel: [35005.981909] Buffer I/O error on device sr0, logical block 2066374
Oct 30 20:39:51 ub-desktop kernel: [35005.981914] Buffer I/O error on device sr0, logical block 2066375
Oct 30 20:39:51 ub-desktop kernel: [35005.981920] Buffer I/O error on device sr0, logical block 2066376
Oct 30 20:39:51 ub-desktop kernel: [35005.981926] Buffer I/O error on device sr0, logical block 2066377
Oct 30 20:39:51 ub-desktop kernel: [35005.981932] Buffer I/O error on device sr0, logical block 2066378
Oct 30 20:39:51 ub-desktop kernel: [35005.981937] Buffer I/O error on device sr0, logical block 2066379

```

In Acid rip I will get about 130MB (40 minutes) of the video until these errors come up.  There are usually three or four duplicates of that and then the application closes.  

If I try to copy the files to my hard drive from the mounted DVD it will stall about 30% of the way through and lock the system up.  

I know the errors indicate CRC, but I would assume if the drive was bad I couldn't watch the videos.

Any ideas?

---

### Post by mc4man on 2010-10-30
> but I would assume if the drive was bad I couldn't watch the videos.
Not exactly, when watching there is some error correction possible
(though it does seem like a drive issue if all the disks are failing around the same time.

you could try vobcopy which will work fine if there is no structure protection (try one of your older titles - Heat seems a good testing choice

Basic command for full disk rip
By default vobcopy will attempt up to 10 reads per sector/block before skipping
```
vobcopy -v -m
```

Or (attempts to read in blocks of 16 sectors

```
vobcopy -v -m -F 16
```
====================================================================

(if space isn't an issue and the sole intent is playback then a slight mis-use of dvdisaster may work if all else fails, though more useful for structure protected titles w/ less than 5000 unreadable sectors, not likely your apparent current issue

Edit:
you have checked your dvd's for smudges, scratches ect. particularly near the outer third?
(I believe dual layer dvd's are ripped from inner to outer and then back to inner

---

### Post by wetmonkey on 2010-10-31
Vobcopy worked.  That was the trick.  

I noticed when the copy slowed down the drive sounded like marbles in a can, seeking all over the place.   I am guessing I was wrong that the drive is OK. 

For Team America, it took a little more than an hour to copy the disk.  Not sure how that translates to a 'good' drive. 

Thanks so much for the info!

---

