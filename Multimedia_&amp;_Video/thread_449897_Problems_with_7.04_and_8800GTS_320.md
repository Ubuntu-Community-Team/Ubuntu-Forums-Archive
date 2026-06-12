---
title: "Problems with 7.04 and 8800GTS 320"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by satandole666 on 2007-05-20
Hi all,

I just made the cold turkey switch to linux today.  7.04 is on my laptop and desktop computer (in sig) now.  I've run into my first batch of problems and was hoping to get some help fixing them.

Installing 7.04 went perfectly (if you don't count the fact that the x64 CD didn't play nice with my system, using 32bit instead).  After the first restart I installed the newest updates.  I tried to up my screen resolution and found out I couldn't.  No problem, time to install the graphic card driver.  I used the System->Administration->Restricted Drivers Manager to install the nVidia drivers.  I restarted the computer and the loading bar came up, quickly vanished, then gave me and error with a messed up screen.  It asked me to review the error log of something (I remember X and RGM or RMG or something like that).  After another failed restart I reinstalled 7.04.

The next reinstall went smoothly.  I installed the updates as before and started searching here for answers.  I found this thread:

[http://ubuntuforums.org/showthread.php?t=432056](http://ubuntuforums.org/showthread.php?t=432056)

I followed method #1 to the tee.  No errors or anything and I restarted the computer.  The same error that happened the first time happened again.  Needless to say I am in the midst of a third install.  

So, what am I doing wrong?  How can I install the 8800GTS 320 driver and get it to work?  Thanks in advance.

---

### Post by satandole666 on 2007-05-21
Bueller?

---

### Post by orrorin on 2007-05-22
also try this forum ...

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

cheers!

---

### Post by fwilliams on 2007-05-27
A solution:

Do not add additional screen resolutions during install!

Use symatic (or whatever) to download the libc development libraries and headers (ie. libc6-dev).
[http://www.ubuntugeek.com/how-to-fix...acy-users.html](http://www.ubuntugeek.com/how-to-fix...acy-users.html)

---

