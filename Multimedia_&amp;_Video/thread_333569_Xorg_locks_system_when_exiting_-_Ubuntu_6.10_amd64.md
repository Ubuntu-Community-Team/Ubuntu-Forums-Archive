---
title: "Xorg locks system when exiting - Ubuntu 6.10 amd64"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by Kernel Panic on 2007-01-07
After looking for a few days and not finding an answer, I decided I need to post about this.

I am running Edgy Eft amd64 on my laptop.  Anytime I try to logout, switch users, shutdowd, restart, sleep, or hibernate my system while in X the screen goes black (except for the text curser in the upper left corner), the keyboard stops responding, and I am forced to hard boot the system. This has been happening since the install finished and the system wanted to reboot. 

My laptop is a Toshiba Satellite A105-S4344.   It has an Intel C2D T5500 cpu, 2 GB Ram, a 200GB HDD, and uses the Intel GMA 950 graphics chip.  The xorg.conf states that it using the i810 video driver.  It should be noted that 1.)  I can reboot into recovery mode and use the text consoles without issues, but I cannot cleaning exit X from there either  2.)  Other than this hang, lockup, crash, or what ever you want to call it X and all the other apps I have run in it are completely stable.

I really want to get on with using and customizing my computer, but I am afraid to put much effort into it.  If I keep hard powering the system then sooner or later it won't come back up.

Thanks for reading this.

I will post my Xorg.0.log from /var/logs as 2 replies since it would be too big to fit here.

EDIT:  I can't post the log file sine the forum engine thinks it has too many inage tags. :lol  I'll try to compress it and attach it to a reply.

---

### Post by Kernel Panic on 2007-01-07
Attached to this message is my Xorg.0.log file from /var/log.  

Thanks again for reading all this.  I am a bit unsure what to try or look into next.




KP

---

### Post by Kernel Panic on 2007-01-07
Can someone at least point me to a another forum or website that deals with X issues?



KP

---

