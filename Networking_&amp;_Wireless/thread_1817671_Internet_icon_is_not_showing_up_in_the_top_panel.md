---
title: "Internet icon is not showing up in the top panel"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by poll262 on 2011-08-03
I am running ubuntu 11.04 in classic mode and for some reason the little network icon located in the top panel disappeared. I tried resetting the panels using: 
```
gconftool --recursive-unset /apps/panel &&  killall gnome-panel
```
When I right click and choose add to panel it doesn't show up as one of the options.
I also installed compizconfig and docky then it disappeared. would this have anything to do with this?

---

### Post by ajgreeny on 2011-08-03
I think the icon is now in the indicator-applet or something similar.  I'm not on ubuntu 11.04 so can not check this, so try several panel applets, one by one, until you find it is back.

---

### Post by poll262 on 2011-08-03
I solved this problem by adding a notification area and then restarting my computer then it showed up thanks for the help.

---

### Post by mashdsl55 on 2011-08-19
hey poll262 may you please give a step-by-step process you carried out because i've also unfortunately came across this bug. :-) thanks in advance

---

