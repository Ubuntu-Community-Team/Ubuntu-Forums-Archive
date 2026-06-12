---
title: "another nm-applet problem"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by mabtifro2 on 2008-12-30
like many others on the forum, my nm-applet icon on my toolbar has magically vanished. so why am i posting yet another thread? because it's only missing in the lxde environment, which is my default interface, but is still present in gnome.

i use lxde because its much more responsive on my 900mhz eeepc. i used to be able to view the nm-applet by running that command using alt-f2 but for some reason, it stopped showing up on the toolbar, however, i can see it running when i open system monitor.

and like i said, it's all gravy when i start up in gnome.

i tried uninstalling it and reinstalling, and i tried to run 'sudo nm-applet' from a terminal, but no results.

thanks in advance

---

### Post by mabtifro2 on 2008-12-31
oh, and im running 8.04

---

### Post by mabtifro2 on 2008-12-31
happy new year. any help?

---

### Post by lswb on 2008-12-31
I don't know anythong about lxde, but nm-applet requires a notification area in the DE somewhere. Is there a way to install a system tray or notification area in the lxde environment? 

As I understand it, nm-applet is written to the freedesktop.org system tray area specification which is still evolving, which theoretically allows it to be used by any DE that conforms. Or something like that :)

---

### Post by mabtifro2 on 2009-01-01
omg omg omg omg, i added the system tray and there it is, popped right up, i love you i love you i love you

---

