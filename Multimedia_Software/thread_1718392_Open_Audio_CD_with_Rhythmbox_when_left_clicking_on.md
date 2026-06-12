---
title: "Open Audio CD with Rhythmbox when left clicking on desktop icon, instead of Nautilus"
date: 2011-03-31
forum: Multimedia Software
---

### Post by vezolmi on 2011-03-31
When I have an Audio CD inside my computer in the desktop there is an icon called "Sound disk". When I left click on it Nautilus opens. I would like Rhythmbox to open instead.

I've tried to change in /etc/gnome/defaults.list :
x-content/audio-cdda=rhythmbox.desktop
by
x-content/audio-cdda=rhythmbox-device.desktop

But the problem is still here.

Any ideas?

NB: I only need to click once on the icons of the files to open them (I changed the preference of Nautilus).
NB2: I have no problem with "Open with" in the context menu when right clicking.
NB3: I have no problem when I insert an Audio CD:  Rhythmbox opens automatically because I selected that option.

---

### Post by lidex on 2011-04-01
Seems to be default behavior for some reason. Not sure there is a way around.

---

### Post by vezolmi on 2011-04-03
Thanks. I hope someone knows how to solve this.

---

