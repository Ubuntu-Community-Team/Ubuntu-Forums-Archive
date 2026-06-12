---
title: "Spurious key events in MythTV following upgrade to Hardy 8.04"
date: 2008-05-01
forum: Multimedia Software
---

### Post by jeremybear on 2008-05-01
Since upgrading to Hardy, I have noticed random, spurious keyboard events in MythTV.  The key being "pressed" appears to be the down arrow (code 104) because when leaving MythTV in idle state overnight at the main menu, the highlighted menu item is 2 or 3 lines further down the list when I return to it in the morning.  

In Live TV mode, the problem manifests itself as unwanted "browsing" to the channel below the one currently being watched.

I will try running xev to confirm this is happening as I have described, but does anyone know a way of trapping these events so the culprit can be identified?

BTW, I have disabled lirc which was my first suspect (maybe the IR sensor was  picking up spurious pulses from somewhere) but that did not help.

---

### Post by jeremybear on 2008-05-05
OK, I think I have found the source of my problem.

It was my Advent ADE-WNL2 wireless mouse, which lsusb shows as "062a:0000 Creative Labs Optical Mouse". I do not know if I have a faulty mouse, or if the problem is generic, however it only started after I upgraded to Hardy.

I found the spurious events by creating a log file in my home directory "xev.log" then teeing the output of xev into that file:  
$xev | tee xev.log

I now disconnect my mouse while watching MythTV, and I will be changing the beast very shortly!

---

