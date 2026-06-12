---
title: "Configuring Audigy crashed Gusty"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by TheQuicksilver on 2007-10-23
So, last night I made the jump to 7.10 on my desktop.  I was thrilled, and more than ready to cut most of my last ties to Windows.  The main problem I hit was no sound (using an Audigy Platinum with A64 3200+).  I searched all over, and it looks like this is more isolated than widespread as far as problems go.

I found the instructions at [http://ubuntuforums.org/showthread.php?t=153823](http://ubuntuforums.org/showthread.php?t=153823) and was following them through after trying some other things that hadn't worked.  I got to the line to run...
sudo /etc/init.d/gdm stop
...and when I did it, the system crashed to a black screen.  Now, Ubuntu won't start up.  It just hangs at the loading screen.

I'm new enough to Linux that I can't trouble shoot it like I can a Windows box, so I'm a little lost at where to go or what to do at this point.  Save me!

---

### Post by TheQuicksilver on 2007-10-23
Bump for any thoughts on the problem?

---

### Post by TheQuicksilver on 2007-10-23
I was incorrect.  The problem is actually an ndiswrapper issue.  Corrected thread: [http://ubuntuforums.org/showthread.php?t=589068](http://ubuntuforums.org/showthread.php?t=589068)

---

