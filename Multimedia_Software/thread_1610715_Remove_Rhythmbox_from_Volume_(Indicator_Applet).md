---
title: "Remove Rhythmbox from Volume (Indicator Applet)"
date: 2010-11-01
forum: Multimedia Software
---

### Post by newbiz on 2010-11-01
I was wondering if there is some kind of way of removing the rhythmbox link in the volume menu in the indicator applet..
It's just that I hardly use it and it's pretty annoying and redundant as well having it there. I don't want to get rid of the volume menu completely nor of rhythmbox. I just want the link gone from there. Actually it never was there until I decided to open it once. After that day, it wouldn't go, no matter how I would exit the program. I didn't have this problem in 10.04. It's just in 10.10.

---

### Post by mc4man on 2010-11-01
i believe you'd need to either re-build the current maverick rhythmbox source or revert to a slightly older version
see here
[http://ubuntuforums.org/showthread.php?p=10013147#post10013147](http://ubuntuforums.org/showthread.php?p=10013147#post10013147)

---

### Post by wanchai on 2010-11-14
see here: [http://ubuntuforums.org/showpost.php?p=10012561&postcount=5](http://ubuntuforums.org/showpost.php?p=10012561&postcount=5)

delete *~/.cache/indicators/sound/familiar-players-db.keyfile*, then restart the panel with *killall gnome-panel*

If you prefer a simpler volume control, see here: [http://www.ubuntugeek.com/how-to-remove-and-restore-the-volume-button-from-system-tray.html](http://www.ubuntugeek.com/how-to-remove-and-restore-the-volume-button-from-system-tray.html)

---

### Post by mc4man on 2010-11-14
> see here:....
As mentioned in the edit rhythmbox will return, that list is only good for adding apps one wished to open from sp (the only apps that can be controlled in sp atm are  - amarok2, banshee, rhythmbox 

The way to remove is posted previously (don't see the point though..

---

