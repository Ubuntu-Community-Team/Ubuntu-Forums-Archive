---
title: "Converting mp3 to ogg causes system to shut down"
date: 2009-12-19
forum: Multimedia Software
---

### Post by wupp on 2009-12-19
I am having an issue with my system (8.04) and converting mp3 audio files to ogg format.  When I try to use mp32ogg on a directory, the whole system will restart.  I have tried the Sound Converter program, and again, if I try to do an entire directory, the system will restart.  If I do just 6 files at a time, it seems to be ok.  However, when I get to the 4th set of 6 files, again the system will restart.  

What is going on with my system?  Is there a particular log file I can look at to see what might be happening?

Thanks!

---

### Post by lloyd_b on 2009-12-19
> **wupp said:**
> I am having an issue with my system (8.04) and converting mp3 audio files to ogg format.  When I try to use mp32ogg on a directory, the whole system will restart.  I have tried the Sound Converter program, and again, if I try to do an entire directory, the system will restart.  If I do just 6 files at a time, it seems to be ok.  However, when I get to the 4th set of 6 files, again the system will restart.  

What is going on with my system?  Is there a particular log file I can look at to see what might be happening?

Thanks!

One suggestion - from the Grub prompt, run Memtest.  If you have a flaky memory stick, but that memory location isn't accessed until you push the system by running the converter, then it would account for this failure.

Lloyd B.

---

