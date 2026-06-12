---
title: "Update manager always runs/pops up when front end it booted"
date: 2009-09-26
forum: Mythbuntu
---

### Post by nunrgguy on 2009-09-26
Any pointers on how to stop this - the update manager alweays pops up and has focus.

I've tried gconftool -s --type bool /apps/update-notifier/auto_launch false
and also switched of the update notifier in system settings but I still get the popup.

---

### Post by klc5555 on 2009-09-26
> **nunrgguy said:**
> Any pointers on how to stop this - the update manager alweays pops up and has focus.

I've tried gconftool -s --type bool /apps/update-notifier/auto_launch false
and also switched of the update notifier in system settings but I still get the popup.

Sounds like the desktop settings were saved with the update manager running. Try closing update manager on the desktop. Then do a "log off" out of X, but make sure the box "save settings" is checked. When X respawns, update manager shouldn't start.

---

### Post by nunrgguy on 2009-09-27
That did the trick

Many thanks
:popcorn:

---

### Post by neutron68 on 2009-10-07
THANK YOU! :D

That worked for me too!

Eric

---

### Post by ReddogOne on 2009-10-09
Its great to stop the update manager popping up but is there somewhere to get it to pop up only when you first switch the box on. So at least you get the prompt once in a while.

---

