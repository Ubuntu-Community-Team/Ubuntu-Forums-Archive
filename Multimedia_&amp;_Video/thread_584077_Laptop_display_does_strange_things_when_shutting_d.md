---
title: "Laptop display does strange things when shutting down or changing to shell mode"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by jimbodude21 on 2007-10-20
I'm running Gusty with nVidia drivers on a Sony VGN-S480 laptop, which has an nVidia Go 6200 onboard.  I have the latest versions of all packages installed.  This has been happening since I installed Gusty Beta on this system about a week ago.  I've waited until the official release to see if it would be fixed before posting.

Whenever I change from graphical mode to shell mode (Ctrl+Alt+F1) the display does some strange things.  It will keep some of the pixels of whatever was being displayed right before changing to shell mode, other pixels will turn black, others full green or full red.  While this is going on, I'm not able to see anything useful on the display.  This combination of Gnome desktop and random pixelation does not change or go away no matter how long I wait.  If I reactivate graphical mode (Ctrl+Alt+F7) the screen returns to normal.

A similar thing happens when I shut down, except that the strange pixelated image will slowly fade to white, and sometime black vertical stripes will appear.  I do not see anything that would normally be displayed on shutdown at any point.  Sometimes, the system will not shut down completely, and the display will continue to show the pixelated image of the desktop, or some other random pattern.

I'll try to attach some photos of exactly what this looks like later tonight.

Any thoughts or suggestions are appreciated.

---------------------------------------------------------
EDIT:
I've found that using the "nv" driver instead of the "nvidia" driver fixes this problem.

I've taken some photos of what this looks like, but the file size restriction on the forum's attachments would require me to shrink them beyond a useful size.

---

