---
title: "remote desktop"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by Prium on 2009-06-29
UNR 8.10 is running on my eeePC. What I want to do is control it remotely from another PC running Intrepid. 

The problem is that the 'remote desktop' feature is missing from my Preferences menu in UNR 8.10. In normal Intrepid it is there. 

Werid, because:
a) xvnc4viewer and vino are both installed
b) these guides say it should be there:
[http://gnomejournal.org/article/29/remote-desktop-administration-using-vino](http://gnomejournal.org/article/29/remote-desktop-administration-using-vino)
[http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html)
c) and GNOME Remote Desktop Server is running

Any idea on what could be missing?

---

### Post by jhannah on 2009-06-30
It might simply be disabled in your menu preferences, check out System -> Preferences -> Main Menu and see if it is unchecked in there. If not, I would double check to make sure vino is installed (which is the Gnome VNC server). Part of that package should include the 'vino-preferences' command which is effectively what is run when you click menu shortcut anyway.

That being said, I wouldn't generally recommend using VNC as it can be pretty frustrating after awhile. You might want to check out FreeNX ([https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)). It takes a little longer to setup but is leaps and bounds better than VNC.

---

### Post by Prium on 2009-07-01
Thanks I wasn't aware of FreeNX. 
I decided to ditch UNR 8.10 and install the full version of Jaunty in its place. The little machine actually runs a bit better now AND I managed to set it up as a remote desktop host. Works beautifully.

---

