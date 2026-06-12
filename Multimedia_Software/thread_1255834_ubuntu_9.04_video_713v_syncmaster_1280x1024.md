---
title: "ubuntu 9.04 video 713v syncmaster 1280x1024"
date: 2009-09-01
forum: Multimedia Software
---

### Post by harrismh777 on 2009-09-01
Greetings,
I need some help.  I have a Samsung 713v syncmaster that will not display 1280x1024@60.  I am running 9.04 jaunty and can display the modes below 1280x1024.  When I change the resolution to 1280x1024 the screen goes blank; yet, the desktop is there, and I can manipulate it, as in the dark, as it were.

I really think the default video modes set at the factory have been clobbered, at least for 1280x1024.  I tried the OSI to reset the modes to factory default, but no good... at least, xorg on ubuntu 9.04 cannot display to it. 

Any ideas?

PS  xorg.conf shows completely default.    :confused:

---

### Post by harrismh777 on 2009-09-10
> **harrismh777 said:**
> 

I really think the default video modes set at the factory have been clobbered, at least for 1280x1024.  I tried the OSI to reset the modes to factory default, but no good... at least, xorg on ubuntu 9.04 cannot display to it. 

*resolved*
Holding the OSI Menu button and then pressing and holding the power button together with the menu button until the menu goes out unlocks the display and restores the factory (or last) mode lines. (this is not in the manual, by the way)
I was able to get the monitor working reliably again at 1024x768, but still not reliably at 1280x1024.  Appears that the driver board has been damaged to some extent.  I did try xrandr and gtf in an effort to create a new modeline that would match and be reliable but after several hours of playing decided to give up.  I have locked the display at 1024x768 and use it as the spare.

---

