---
title: "Config files for Unity Launcher on Natty?"
date: 2011-03-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by r-senior on 2011-03-11
Does anyone know where these are?

This is a fresh install of Ubuntu 11.04 Natty Alpha 3. 

I've looked at various blog posts and dug around in my home directory to no avail. All I find in ~/.local/share/unity is a log file that seems to show attempts to migrate launcher items from Docky et al. The directory ~/.gnome2/panel2.d/default/launchers is empty.

I've looked in gconf editor but can't find anything there either.

I raised a bug ([#732733]("https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/732733")) about the launcher not working with Netbeans once it is pinned in the launcher but it seems like a Unity issue because it's the same with Gimp. I was going to see if I could figure out a workaround but can't any config.

As a side issue I also note that my Unity window has shortcuts for "Check EMail" and "Listen to Music" but both these open Firefox. Anyone know where these are configured?

---

### Post by kerry_s on 2011-03-11
i think i saw them in dconf-editor before, not sure if there in there now.

forgot to mention, the last time i tried dconf-editor it would lock up.

ps: you know you can drag & drop from the file manager /usr/share/applications straight to the launcher, easiest way to get the apps on the launcher with out opening each 1.

---

### Post by r-senior on 2011-03-11
You are quite right, dconf-editor has it.

And no I didn't know I could drag to the panel like that. I've had problems with Compiz crashing when I start dragging things around, so I'll press Submit Reply before I try it. :D

Many thanks.

EDIT: That worked from /usr/share/applications and it's also partly fixed the problem with Netbeans not launching off the panel. Still get an extra icon, so I'll go off and update the bug.

---

