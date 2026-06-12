---
title: "Wasp theme"
date: 2011-01-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by laebshade on 2011-01-22
Upgraded to 11.04 last week.  Went to reapply the Wasp theme ([http://gnome-look.org/content/show.php/Wasp?content=104167](http://gnome-look.org/content/show.php/Wasp?content=104167))... it only changed the window decoration; no controls, GDM theme, the gnome panel, etc.  Anyone else use this old theme?  It took me through lucid and maverick, though it wasn't officially compatible with maverick, it worked fine with no glitches.  I wonder what the difference between maverick and natty is that is preventing it from working? (rhetorical question)

I'll be trying the official developer, of course, just want to see if anyone else is running it successfully on 11.04, and if so, how they did it.

---

### Post by Harry33 on 2011-01-23
> **laebshade said:**
> Upgraded to 11.04 last week.  Went to reapply the Wasp theme ([http://gnome-look.org/content/show.php/Wasp?content=104167](http://gnome-look.org/content/show.php/Wasp?content=104167))... it only changed the window decoration; no controls, GDM theme, the gnome panel, etc.  Anyone else use this old theme?  It took me through lucid and maverick, though it wasn't officially compatible with maverick, it worked fine with no glitches.  I wonder what the difference between maverick and natty is that is preventing it from working? (rhetorical question)

I'll be trying the official developer, of course, just want to see if anyone else is running it successfully on 11.04, and if so, how they did it.

The incompatibility could be caused at least because of different cairo (libcairo2) or GTK+2.0. Did you test Gnome-Classic? Compiz?

---

### Post by MacUntu on 2011-01-23
Does this happen just with this one theme? If other (official) themes fail too, you're maybe hitting this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296)

---

