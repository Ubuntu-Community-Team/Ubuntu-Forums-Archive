---
title: "name of standard connection manager prgrm ??"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by zakie-chan on 2009-01-16
Im a fairly recent linux user running intrepid, gnome. Im in the process of reproducing the OS X look to tease my sister with my mighty linux.

In the process of being accurate i removed the standard internet connection manager from the top panel... in its place i put the network monitor.I thought i could manage my connections just by selecting the standard program from the menu but i cant find it!!

Can someone tell me the name of the wireless/ethernet connection manager that comes standard with gnome and how can i find it/get it back on the panel ????

sorry for sucking, ill do better...

---

### Post by MaindotC on 2009-01-16
It's just called nm-applet.  You can run it from the command line.  If you want to add it back to the panel just right-click and click "add to panel" and the custom launcher will be nm-applet.

---

### Post by zakie-chan on 2009-01-16
i did this...


zakie-chan@Little-Lucy:~$ nm-applet

** (nm-applet:8349): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:8349): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

And returned that error, am i doing this right?
sorry but im a newb, advice what to do next ?

---

### Post by MaindotC on 2009-01-17
Hmmm...when I start mine I don't have any problems - even without launching it as root.  Can you try rebooting and then launching nm-applet?

---

