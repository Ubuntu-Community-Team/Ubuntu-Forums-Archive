---
title: "Private Network &amp; Wireless gone after Upgrade"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by marort on 2009-06-08
After upgrading from 8.04 to 8.10 my private network settings and my wireless are gone.

I used to be able to view or to manage both of these settings in 'Network Configuration' (Gnome) but after the upgrade they both disappeared from the gui tool. However, if I run a 'ifconfig' command in the terminal it still showing my wireless setting.

In addition to this, I am still able to access my private network without any problem.

Should I just re-configure these settings on top of the old or is there something better I could do?

Thanks in advance for all your help.

---

### Post by quixote on 2009-06-09
Do you mean that the little ethernet/ wireless icon has disappeared from the system tray area? (Or panel, or whatever it's called.)  Or that nm-applet itself has disappeared (eg you can't run it from a terminal)?

The icon disappears if you don't have a "notification area" in your panel.  (Not exactly intuitive.)  Right click on an empty part of the panel, and select "add to panel".  When the choices pop up, scroll down to "notification area" and add it.  You can move the set of icons to wherever you want by dragging.  (If they won't drag, right click and untick "lock to panel".)  There's no choice except to have the whole set, even if all you want is the wireless icon.

If nm-applet itself somehow got uninstalled, you can re-install that via synaptic.

---

### Post by marort on 2009-06-13
Thanks for your response Quixote, but the problem is not the icon on the task bar. It is just weird that after upgrading (from 8.04 to 8.10) my network settings disappeared from the Network configuration in the graphical interface.

Both Internet and my LAN are still up, but they do not show in the graphical tool. If I go to the terminal I can see the connections just fine.

Perhaps the only thing I can do is to remove using the terminal and to reconfigure graphically. Not sure this will work.

---

### Post by quixote on 2009-06-14
I should have mentioned that there's a really long thread on wireless by wieman01: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) called HOWTO: Wireless, and it really is.  His tut was what I used to get up and running in the far-off days of 2006 and it really works.

I hope it helps you too.

---

