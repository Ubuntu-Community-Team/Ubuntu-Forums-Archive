---
title: "Video issue.."
date: 2008-09-21
forum: Multimedia Software
---

### Post by Nettoyer on 2008-09-21
If I try to watch movies off of my computer in VLC or any media program, they flicker badly.
I got the sound working and got my card setup, it's an ATI Radeon X1950 Sapphire PCI-E card.

If you need more info let me know the command to execute.. im a bit of a newb.

---

### Post by stephanvaningen on 2008-10-19
Can you try this, and compiz should work while still having non-flickering video:
 ```
sudo gedit /etc/X11/xorg.conf
```
In the "Device" section, add:
 ```
Option   "TexturedVideo"   "Off"
```
(source: [http://forum.compiz-fusion.org/showpost.php?p=45637&postcount=5](http://forum.compiz-fusion.org/showpost.php?p=45637&postcount=5))

Remark: On my machine this change [caused this]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/281433"), but that's another thing...

---

