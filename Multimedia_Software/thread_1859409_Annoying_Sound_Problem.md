---
title: "Annoying Sound Problem"
date: 2011-10-13
forum: Multimedia Software
---

### Post by Dan Again on 2011-10-13
I was trying to fix a problem I was having with video playback and came across the following thread...

[http://ubuntuforums.org/showthread.php?t=1266564](http://ubuntuforums.org/showthread.php?t=1266564)

At the suggestion of one of the contributors I edited /etc/rc.local with the following line just before "exit 0"...

chmod 666 /dev/nvidia* &

Now when I first log in to my system I do not have sound. In order to get sound to work I have to go to the Sound Preferences menu and change my output hardware from HDMI to something else and then back to HDMI. This isn't the biggest deal in the world, but I'd like to fix it. Does anyone know why this is happening?

---

### Post by Dan Again on 2011-10-14
I should also mention that the changes I made to /etc/rc.local didn't solve my video playback problem, so I just deleted the line I had added, however the sound problem persists. Any ideas?

---

### Post by Dan Again on 2011-10-14
Well, okay...I seemed to have solved the problem. When I was trying to solve the problem documented in the link in my first post, I came across several people saying that the solution to their problem was to turn the Sound Hardware Profile to off.

Before I did this, I looked in the Comprehensive Sound Solutions Guide and saw that running...

sudo alsactl store 0

will save your settings. I executed this command, but then when I logged back in I could not get sound to work, even after switching my hardware profile. I tried turning the hardware profile off, and voila! My sound worked immediately and now works without adjustment every time I log in.

---

