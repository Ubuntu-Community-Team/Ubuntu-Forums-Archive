---
title: "Can't escape from MythTV front end"
date: 2009-07-15
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-07-15
Normally, if I want to exit from the MythTV front end and go back to the Ubuntu desktop, I simply press "escape" on my keyboard from the main MythTV menu, and after confirming that yes, I am sure, it exits back to the Ubuntu desktop.

But sometimes, it doesn't. A reboot then seems to be needed to get it to work again.

Any ideas what could be going wrong here?

Thanks
NM

---

### Post by newlinux on 2009-07-15
no ideas but you can check the frontend logs to see if something is happening there. Are you running gnome or KDE (not sure if this works in XFCE) -if so you could do a ALT-F2 to get the run command dialog and then type in ```
killall mythfrontend.real
``` instead of rebooting.

---

### Post by NautiusMaximus on 2009-07-16
Many thanks for the tip about the alternative way to exit. That works just fine.

Nothing jumps out from the log files as pointing to a cause, although there's a lot of stuff there. Any ideas what to look for?

Failing that, I'll keep trying to escape on a regular basis so at least I'll be able to narrow down when the glitch occurs.

---

### Post by newlinux on 2009-07-16
No ideas on what to look for, but maybe you can turn up the verbosity of the log and post it here. Maybe someone will notice something. If you use a remote you could also bind a key that kills mythfrontend as well (you could also do this with the keyboard). I do this so I can switch between XBMC and myth using the remote. I know that's a workaround - better to find out the problem and fix it.

---

### Post by Zeedok on 2009-07-18
This happens to me occasionally as well.  You might consider this as a strategy to deal with it:

I have two desktops setup, so if I want to get on the internet etc I just slide over to the other desktop etc etc.  It's good if you want to look something up in the ad break!  If mythTV crashes, I just slide over and kill it there.

---

