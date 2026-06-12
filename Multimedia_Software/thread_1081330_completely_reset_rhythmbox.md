---
title: "completely reset rhythmbox"
date: 2009-02-26
forum: Multimedia Software
---

### Post by fisherm on 2009-02-26
I need to completely redo my rhythmbox setup I think. I had moved some custom icons into /usr/share/rhythmbox/icons etc...and they didn't work out right. So i deleted them and restarted rhythmbox, and they are still there. so I "sudo aptitude purge rhythmbox" and it was removed. Then I reinstalled it and it still uses the icons I deleted. I just want rhythmbox !completely! gone so I can start over as if it were my first time running it. Any help greatly appreciated.

By the way, I did delete .gnome2/rhythmbox and ~/.config/rhythmbox

---

### Post by smani on 2009-02-26
I'd suggest, have a look at what files are installed by the package:
```
apt-file list rhythmbox
```
and then search and delete them manually. It can occur that if you move files around manually in the installation location, then the package manager can lose track of the files installed.

---

