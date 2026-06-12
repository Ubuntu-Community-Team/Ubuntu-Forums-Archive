---
title: "xvidcap screen recording zero byte output"
date: 2009-11-28
forum: Multimedia Software
---

### Post by rdd37 on 2009-11-28
Hello,

I've installed xvidcap from the repositories. I then also installed libavcodec-unstripped-51 to resolve an issue with the application immediately crashing (as per [http://ubuntuforums.org/showthread.php?t=888724](http://ubuntuforums.org/showthread.php?t=888724)). 
While the application seems to be recording now (it runs successfully until I tell it to stop), the resulting video output file is always zero (0) bytes. 
The only troubleshooting information I could find about this (which is not about the exact same issue) is [here]("http://sourceforge.net/apps/mediawiki/xvidcap/index.php?title=Faq#xvidcap_hangs_on_starting_a_capture_session._What_can_I_do_about_it.3F") This suggests that since my linux distribution uses libxcb, it could cause a multitude of problems. Neither of the two resolution options appeal to me, so if this is the case, I will try a different screencasting application.

Does anyone have any other input about this zero byte output issue though?

thank you.

---

### Post by rdd37 on 2009-11-29
Unfortunately I cannot locate any logs for this application to try to troubleshoot. Nothing in /var/log/, and I don't see a file or hidden directory in the user's home like with some other apps..

does anyone know if xvidcap logs at all?

---

### Post by rdd37 on 2009-11-29
I tried Istanbul (from the repositories) instead.
I first received "recording open error on device 'default' connection refused" errors, when trying to record with audio. When I disabled audio recording, Istanbul froze during capture, and I could not find any output file. 

So I moved on to recordmydesktop. The video capture is working great, but no audio as of yet. I'm going to try messing with audio settings now.

---

### Post by rdd37 on 2009-11-29
> **rdd37 said:**
> 
So I moved on to recordmydesktop. The video capture is working great, but no audio as of yet. I'm going to try messing with audio settings now.

Still no audio on the system I'm trying to get this to work on. I've skimmed [this]("http://ubuntuforums.org/printthread.php?t=294605&pp=75") entire thread, and the advice that sticks out (seeming to solve most peoples' lack of audio in recording issue) is:
install and run gnome-alsamixer
check the checkbox mix

I installed gnome-alsamixer, but the system I'm working on does not have a 'mix' checkbox to enable. 

So I tried this on another system, which does have the 'mix' option. I enabled that, and recordmydesktop works flawlessly.


Any ideas why this system would not have a 'mix' option? Insufficient sound card? Any other options to make this work?

---

### Post by rdd37 on 2009-11-29
Any ideas? 
If not I may re-post this question under a separate thread since I can't seem to change the thread subject line.

Thanks.

---

