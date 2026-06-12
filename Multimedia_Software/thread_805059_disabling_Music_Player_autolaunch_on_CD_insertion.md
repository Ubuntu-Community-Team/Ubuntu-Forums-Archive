---
title: "disabling Music Player autolaunch on CD insertion"
date: 2008-05-23
forum: Multimedia Software
---

### Post by BetterSense on 2008-05-23
I'm sure this is a simple fix, but how do I make my system do nothing, yes, nothing when I put in a CD? It always launches Music Player, but I only use mplayer or sometimes Amarok.

---

### Post by NT4usB on 2008-05-23
In a terminal:```
gnome-volume-properties
```or find it in System>Preferences...

---

### Post by BetterSense on 2008-05-23
I already tried that. Nothing is enabled, except the photo-program is set to launch when I plug in a camera.

---

### Post by nick_h on 2008-05-23
System->Preferences->Preferred Applications

---

### Post by mc4man on 2008-05-23
It depends on what version your using. 7.04, 7.10 - .system -> preferences -> removable drives and media
8.04  edit menus -> enable file management in preferences then go there under media tab

---

### Post by khoover on 2011-05-01
How do you remove entries from the media autolaunch menu? I'm using 10.10, and I'd like to remove custom commands that I've tried in the past.

---

### Post by mc4man on 2011-05-01
home folder > (view -show hidden files) > .local >share > applications
 You'll find mimeapps.list, remove the userapp-name-XXXXXX.desktop entires on the appropriate lines (where name usually is the first word of command, XXXXXX is random

Also in that folder will be the corresponding userapp .desktops that can also be removed

(if you wish to start completely over just delete the mimeapps.list file or even everything in the applications folder

---

