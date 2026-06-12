---
title: "Audio/video sync issue while appending several mpeg files"
date: 2010-04-30
forum: Multimedia Software
---

### Post by linuxyogi on 2010-04-30
Hi, 

My problem is 


When I try to encode several mpeg 2 (DVD Video) files by opening a file & 

"appending" the rest of them from the same folder & try to encode them to 

XVID, I get an audio/video sync problem.



This problem occurs only when I try to encode several video files together by appending them.

I am using avidemux to backup (encode) my DVDs.

Is there a way to fix this ?

---

### Post by ron999 on 2010-04-30
Hi
If those mpeg2 files are VOBs in a VIDEO_TS folder then you can extract them as one file using **vobcopy** from Ubuntu's repo.
Then encode the one file to XVID.

---

### Post by linuxyogi on 2010-05-01
> **ron999 said:**
> Hi
If those mpeg2 files are VOBs in a VIDEO_TS folder then you can extract them as one file using **vobcopy** from Ubuntu's repo.
Then encode the one file to XVID.

Thanks for your reply. I just installed vobcopy. 

But the problem is vobcopy can extract the vob files from a mounted DVD only. It doesn't accept path to the VIDEO_TS directory (manually).

Some of my DVDs are badly damaged & are hardly readable. I have somehow managed to copy them to my hard drive.

I guess I will have to encode them part by part.

Thanks again.

---

### Post by mc4man on 2010-05-01
While it's been awhile I believe vobcopy will 'rip' from a mounted .iso, you could give that a try if no other means presents itself.

small note:
thru a 'slight' misuse of dvdisaster you can recover dvd video disks to an encrypted iso (if css is present),  which then can be played back as is, or mounted and ripped/transcoded, whatever

---

