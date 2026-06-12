---
title: "Merging files"
date: 2009-09-07
forum: Multimedia Software
---

### Post by PureLoneWolf on 2009-09-07
Hi all

I have searched, but not found a successful solution to this.  I have a number of files that need to be joined together.  I have tried:

avimerge (which results in massively out of sync merged files)

mencoder (which fails as the files aren't identical resolutions)

ffmpeg (which worked perfectly, but took 3 files totalling 216mb and created a merged file of 1.4gig)

Does anyone have a good solution?  Doesn't have to be gui based

Thanks

---

### Post by andrew.46 on 2009-09-07
Hi PureLoneWolf,

> **PureLoneWolf said:**
> ffmpeg (which worked perfectly, but took 3 files totalling 216mb and created a merged file of 1.4gig)

Did you follow the technique mentioned in the FAQs:

3.18 How can I join video files?
[http://ffmpeg.org/faq.html#SEC30](http://ffmpeg.org/faq.html#SEC30)

This in theory should not produce a giant file, but I have been wrong before :-). Did you experiment with the *-c* option of avimerge? Does not sound ideal but this might improve your sync...

All the best,

Andrew

---

