---
title: "SOLVED: How to restore Network Manager to menu panel"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by sharp11 on 2009-01-14
After too much time spent thrashing on this, I finally figured out how to restore the nm-applet to the Gnome menu panel. I documented it here:
[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

(It could still benefit from documentation for non-Gnome desktops.) Here's the text:

If you're missing the Network Manager panel applet, then (in Gnome) make sure that your panel contains the Notification Area applet. (Right-click on the panel to access the "Add to panel" command.) The NM applet can't be added directly to the panel, but is automatically part of the Notification Area. If you already have a Notification Area, but still no applet, then make sure the applet is installed. Just bc you have Network Manager does not mean you have the panel applet. Installing network-manager-gnome and restarting your system should make the panel applet appear in the Notification Area.

---

