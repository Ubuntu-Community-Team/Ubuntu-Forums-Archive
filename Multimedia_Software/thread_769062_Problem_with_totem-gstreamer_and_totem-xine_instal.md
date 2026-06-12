---
title: "Problem with totem-gstreamer and totem-xine installed together"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Radomir on 2008-04-26
It's an upgrade from gutsy x64 - pretty much clean installation, upgrade went smooth. Installed totem-xine trough synaptic, enabled medibuntu and installed libdvdcss2 and some upgrades and then went on with my plan: 
sudo update alternatives --configure totem or /usr/bin/totem-xine or 
/usr/bin/totem-gstreamer - enabled it trough alacarte, too. Plan is to use totem-xine for dvd playback, and totem-gstreamer for xvid - i.e. to switch between them when i need one or the other. But, when I switch to totem-xine and then back to gstreamer - colors are messed up. Everything is blue. Same happens when I play both totems at the same time - colors are wrong. And then, all the colors are wrong - only way I can recover from that is to delete .gconf and .gconfd and logout - login again. Is there a way to use both totems at the same time? 
Hardy x64
XFX 8600 GT
Tvinview enabled and working...

---

### Post by cor2y on 2008-04-26
Its not the player its a bug in the closed source nvidia drivers and congrats on getting yours to work :)
To fix this simply go to preferences in totem (doesn't matter which one xine or gstreamer) and adjust your hue video settings either to the max or min and now the colors should be correct.

---

### Post by Radomir on 2008-04-26
Tried that before I wrote, but it does not work... At least here. Or do I need to restart playback or totem after adjusting hue0? Btw, are the drivers in the repository latest nvidia drivers and are there newer drivers with a fix for this... I'm willing to try manual installation :D. And thanks very much!

---

