---
title: "Cant access Sound preferences"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by vonda on 2008-01-05
Hi Guys

I have a problem opening some applications. Its a fresh install of ubuntu 7.10 and i get an error about Gnome settings when i log in but im new to Linux and dont know where to look for more information.

Sound plays fine but i cant access Sound Juicer or sound preferences. They start to load but then dissappear. It says Starting Sound down on the task bar but then nothing happens. I also cant access Add/Remove.

Is there something i can do to re-configure gnome to get my applications to work?

Thanks

---

### Post by Yellow Pasque on 2008-01-05
After you attempt to load one of those apps, fire up a terminal and type dmesg
Perhaps there are useful error messages towards the end.

You can also access your sound prefs with gconf-editor (similar to Windows' "regedit"). sudo apt-get install gconf-editor if necessary. Just type gconf-editor in a terminal and pull down the desktop and gnome entries and click on sound. Over in the right pane, you'll see some sound prefs.

---

