---
title: "Ubuntu update broke screen resolution"
date: 2012-11-27
forum: Multimedia Software
---

### Post by DMcCunney on 2012-11-27
Okay, this is annoying.

I'm running Ubuntu 12.04 LTS.  The box it's installed on uses onboard Intel video, and I normally use XFCE4 as my desktop.

I have a 27" AOC monitor that uses 1920x1080 as the standard resolution.  It was a replacement for a failed Viewsonic, and I was delighted when I attached it and Ubuntu detected the resolution and used it.

It worked fine until half an hour ago, when Update Manager informed me there were updates and I installed them.  One broke screen resolution: Ubuntu now refuses to admit the monitor will do more than 1024x768. 

I recall having this issue before on another machine that did 1280x768 native, and a Ubuntu 11 series update reduced it to 1024x768.  I never was able to track down what the problem was - poking around in system logs showed that Ubuntu knew the hardware could do the higher resolution, but nothing I did from the desktop would make it do so.  The problem got resolved in a subsequent release.

Is there a known fix for this?  Upgrading to 12.10 is not currently an option. 

Thanks in advance.
______
Dennis

---

### Post by DMcCunney on 2012-11-27
And this may be even more annoying.  

Googling on related issues pointed me at some things I could try.  When I switched back to the Ubuntu box, the problem had mysteriously solved itself.  Suddenly, 1920x1080 was was a resolution selectable from the display properties box, and I could set it and have things back to normal.

No, I have no idea what was going on.  No, I have neither the time nor energy to dig around and find out.  I have a correctly configured box again, and I'll settle.

Consider this solved, and sorry for the waste of bandwidth.
______
Dennis

---

