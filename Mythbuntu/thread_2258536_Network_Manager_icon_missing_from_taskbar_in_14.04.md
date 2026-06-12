---
title: "Network Manager icon missing from taskbar in 14.04"
date: 2014-12-28
forum: Mythbuntu
---

### Post by MoebusNet on 2014-12-28
I thought I'd share the solution to a problem I found with Mythbuntu 14.04: the networking icon for nm-applet is missing from the upper-right of the taskbar, making networking management unnecessarily difficult.

The problem is that nm-applet will presently only launch as root.

To fix this:

```
 sudo gedit /etc/xdg/autostart/nm-applet.desktop 
```

(If you prefer a different text editor, replace gedit with nano or the text editor of your choice.)

Go down to the **Exec** line and change the entry from **nm-applet** to **dbus-launch nm-applet**

Save the file and reboot!

This is working for me in Mythbuntu 14.04 version 0.27 w/updates.


Special thanks to Adz from AskUbuntu for this solution.

---

### Post by agamotto on 2015-01-03
Thanks for this quick tip... this has been annoying me for some time.

---

