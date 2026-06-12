---
title: "Nvidia xorg.conf causes big crashes when changed."
date: 2009-08-10
forum: Multimedia Software
---

### Post by Isaacgallegos on 2009-08-10
When ever I try to edit the file xorg.conf and restart my display drivers fail to start when ubuntu boots. I've been trying to find a thread on this issue. 

The change I've been making is pretty simple: Save my dual monitor setup so that ubuntu remembers it on restart. 

But every time I manage to save the new settings to xorg.conf I get a big trainwreck.

edit:
I have no trouble restoring xorg.conf to stop the crashes.

---

### Post by Isaacgallegos on 2009-08-11
Update. 
I still have not found a thread on this issue. If any find one please let me know.

---

### Post by Isaacgallegos on 2009-08-13
shi-bump.

---

### Post by linuxuser21 on 2009-09-09
What version of Ubuntu are you using?  I've had somewhat of the same problem; however, mine was with ATi.  Once Ubuntu 9.04 came out, all of that seemed to be fixed.  It can now pick up both screens in the "display preferences" as well as the nVIDIA Control Panel.

---

### Post by Isaacgallegos on 2009-10-10
This has been solved. 
The real problem was I couldn't save to xorg.conf on nvidia-settings. So I was editing xorg.conf
What I should have done was use gksu nvidia-settings in the run application window or gksudo nvidia-settings in the terminal to be able to save to the xorg.conf file. 

Now I have a new problem that's in this thread:
[http://ubuntuforums.org/showthread.php?t=1136205](http://ubuntuforums.org/showthread.php?t=1136205)

---

