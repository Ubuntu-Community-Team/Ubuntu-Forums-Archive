---
title: "CDs burned won't play in some players - OK in others"
date: 2013-11-28
forum: Multimedia Software
---

### Post by w9wi on 2013-11-28
I have a 2007 Ford Focus which will play both ordinary audio CDs and CDs containing MP3 audio files.  MP3 CDs burned with my old system (running an embarrassingly old version of Ubuntu) play fine in the car.

I recently upgraded to a new system (new hardware) and Ubuntu 13.04.  MP3 CDs burned with the new system won't play in the car -- it says "BAD DISC" and ejects the CD.

The same CD plays just fine in the Windows 7 computer on my desk at work.  Older MP3 CDs, burned with the old system, still play fine in the car.  I am using the same stock of blank disks I used with the old machine.

I've tried both Brasero and dragging files onto the recordable CD folder, same results.

I was thinking maybe the disks weren't being finalized, but running **cdrecord -fix -dev=/dev/dvdrw** makes no difference -- it finalizes the disk without errors but the disk still won't play in the car.

If I burn the disk as an audio CD, it works fine.  (but of course I can't fit nearly as much music on one disk)

Ideas?

---

### Post by rackit on 2013-11-28
Try burning at a slower speed. This has worked for me.

---

### Post by w9wi on 2013-11-28
That was it - thanks!

They burn by default at 40x - I retried at 24x & it works fine.  Strange that the same 40x disk plays properly on a PC.

(and Happy Thanksgiving to a fellow Badger! - yes, the "wi" in the ham radio callsign I use for a handle *does* mean I grew up up there...)

---

### Post by rackit on 2013-11-28
Some players are more sensitive to burnt speed - particularly car systems and boom boxes. Happy Thanksgiving to you too! I'm a transplant from Colorado about 15 years ago.

---

### Post by mörgæs on 2013-11-28
Please mark the thread 'solved'.

---

