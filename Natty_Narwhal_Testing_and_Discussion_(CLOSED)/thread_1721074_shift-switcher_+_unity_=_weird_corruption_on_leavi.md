---
title: "shift-switcher + unity = weird corruption on leaving switcher"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Zorgoth on 2011-04-04
As depicted in the screenshot, the unity interface becomes corrupted while leaving shift-switcher.  It then fixes itself after the animation is complete.  I'm using an ATI Mobility Radeon HD 5470 with the new ATI driver from the repository (fglrx 2:8.840-0ubuntu1)

Note that the other windows in the screenshot are actually normal - they just happened to be zooming (due to leaving shift switcher) at the time I took the screenshot.

Easy to reproduce - just turn on shift-switcher (which I think is in compiz-fusion-plugins-extra, but possibly is in compiz-fusion-plugins-main) and try to use it with unity, and it will be obvious.

---

### Post by Zorgoth on 2011-04-04
It's actually worse - if I use shift-switcher to switch to an application, it will not show any typing or selecting or anything as having occurred unless I do something to the window like resize it.  So basically shift switcher can't be used.

---

### Post by mc4man on 2011-04-04
It works here pretty well, though am using nvidia.
While there where no issues while using or exiting, a couple of times did seem to cause some issue after using when opening some of the windows normally.
(was late last night, didn't ck. to see if any crash logs were created and have since cleared the folder (/var/crash

(have you tried it when logging into Classic? (gnome-panel

---

