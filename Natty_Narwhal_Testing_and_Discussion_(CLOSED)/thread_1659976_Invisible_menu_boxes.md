---
title: "Invisible menu boxes"
date: 2011-01-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jmmL on 2011-01-04
I've been having this problem on-off with natty for a while. Now it's only "on". If I click something that opens a drop-down menu it doesn't appear. However if I click in the area where the invisible menu is it can still trigger an action.

An example would be clicking "other bookmarks" in chromium. I would then click a few centimeters down on the screen, and it'll take me to one of my bookmarks. To be clear: this happens across all programs. The network indicator, sound indicator, time indicator, firefox, chromium, gnome-terminal are all affected.

Which package is likely to be causing this? Is there an extant bug report?

---

### Post by nm_geo on 2011-01-04
Might be this one>

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/695763](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/695763)

If you right click in background and move to upper panel, do they now start working?

Yep it appears to be the same bug and has been duplicated also..  
Try the right click in the background main screen and make no selection see if you then get 
the drop downs working.

---

### Post by jmmL on 2011-01-04
Looks like that's the bug. It's marked as a dupe though; here's the original: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/695638](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/695638)

So it appears that the menus are just not automatically stacked on the top. The right-click trick works for indicators if there's nothing in the way of the menus (i.e., you don't have a window maximised), but still does nothing for maximised windows and menus for other programs (firefox, chromium etc) are still hidden behind the main program window.

---

### Post by nm_geo on 2011-01-04
> **jmmL said:**
> Looks like that's the bug. It's marked as a dupe though; here's the original: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/695638](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/695638)

So it appears that the menus are just not automatically stacked on the top. The right-click trick works for indicators if there's nothing in the way of the menus (i.e., you don't have a window maximised), but still does nothing for maximised windows and menus for other programs (firefox, chromium etc) are still hidden behind the main program window.

Are you testing from a full installation or USB?  I have the same issue on my installed OS, but after the no-selection right click I can see all my drop downs properly.

---

### Post by jmmL on 2011-01-04
> **nm_geo said:**
> Are you testing from a full installation or USB?  I have the same issue on my installed OS, but after the no-selection right click I can see all my drop downs properly.

I stand corrected. Must've been doing something wrong before. Now the right-click thing works fine. I'm using a full install, upgraded from lucid.

---

### Post by ssam on 2011-01-10
i get this when running of the live cd. very frustrating.

---

### Post by efflandt on 2011-01-11
I get this happening most of the time, which I think corresponds to when I get simple mostly gray icons for the applets in upper right panel and different icons for Unity.  Once in a while when I get Maverick like icons in the top panel and smoother Unity icons, everything works fine.  But when it often reverts to simpler gray icons in upper right panel and different icons for Unity, I have to right click the desktop before menus are visible in top panel and applications and right click works properly for Unity icons.

So maybe a clue is, what sets applet and Unity icons during login and why does that vary seemingly randomly?  For example after Friday night updates everything was fine that night and Saturday.  But without doing any updates since Friday it reverted to gray applets on Sunday, which remained after Monday night updates.

Another odd thing is that with the same nvidia 260.19.29 video drivers, glxgears w/sync to vblank disabled are 32% faster in Maverick than in Natty, even though kworker has been fixed, so idle cpu use is minimal (cpu ave ~1% and uptime in hundredths).

---

