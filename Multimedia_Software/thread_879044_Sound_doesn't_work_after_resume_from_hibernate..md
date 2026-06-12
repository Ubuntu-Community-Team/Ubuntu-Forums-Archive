---
title: "Sound doesn't work after resume from hibernate."
date: 2008-08-03
forum: Multimedia Software
---

### Post by Arathon on 2008-08-03
In 8.04, with the newest kernel updates and everything, sound still doesn't work after resuming from hibernation.  I've tried alsa-utils force reload and things like that.  amixer reports that nothing is muted.  Still, I get no sound unless I do a full reboot.  

What other utilities can I check to see what's actually going on, and what can I do to actually make my sound come back without restarting?

---

### Post by vovven on 2008-08-04
I have the same problem, I tried with:
```
/etc/init.d/alsa-utils restart
```
I also tried some things I found in some old threads, like muting and unmuteing all volumecontols.

Also found a solution with changing in /etc/default/acpi-support
And there set the HIBERNATE_MODE=platform 
 
But it won't work, is the any way to get to sound to work with out rebooting the box?

---

