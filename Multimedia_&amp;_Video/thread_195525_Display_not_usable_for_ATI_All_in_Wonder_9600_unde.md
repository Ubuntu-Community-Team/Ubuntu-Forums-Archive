---
title: "Display not usable for ATI All in Wonder 9600 under Ubuntu 6.06"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by rkline on 2006-06-13
During install for Ubuntu 6.06 on my older system (Athlon64 3000+ with an ATI All in Wonder 9600 videocard), when the CD boots Ubuntu, I do not get a useable display.

Symptoms:
My LCD panel displays a frequency out of range message when the Ubuntu 6.06 boots off of the x86_64 desktop CD
Attempting to change resolution with <Ctrl><Alt>+ either gives an unreadable display where each line is offset horizontally several pixels from the one above it or another frequency out of range

What I've tried and still gotten the same behavior:
- Both the x86_64 and i686 desktop CDs
- Selecting "Start Ubuntu in safe graphics mode" at the boot screen
- Pressing F4 at the boot screen and selecting the panel's native 1280x1024 resolution 

I have used the x86_64 desktop CD to boot Ubuntu 6.06 on my newer Athlon64 3800+ system with an Nvidia graphics card so it does not appear to be a problem with the media.  I've spent about 2 hours trying to search for any reference to this on the Forum and Google.  The search on the forums returns every thread with ATI in it so it didn't narrow things down much, and the posts I read seemed to be mainly issues getting the accelerated drivers to work not failure so severe the system was unusable.  Unless someone has some ideas I'm going to have to punt on Ubuntu.

---

### Post by caldevil on 2006-06-13
In the text mode try running:
sudo dpkg-reconfigure xserver-xorg
and answer the questions, choose resolution, frequency etc. (usually defaults are OK)

If that doesn't work, try selecting the driver vesa instead of any driver like ati or fglrx and see if the problem persists.

---

