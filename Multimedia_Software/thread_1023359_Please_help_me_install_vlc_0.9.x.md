---
title: "Please help me install vlc 0.9.x"
date: 2008-12-27
forum: Multimedia Software
---

### Post by CDiablo on 2008-12-27
I am on Ubuntu 8.04, and have been trying for about 3 hours to get my VLC player from .0.8.6b to any of the 0.9.x versions. I have tried many tutorials online and installed god knows how many packages because of it, but every tutorial that I try gets some error that there is no resolution for on the tutorial page. Can anyone link me to the definitive installation page? Thanks.

---

### Post by SuperSonic4 on 2008-12-27
```
sudo apt-get update && sudo apt-get upgrade
```

oops, forgot to ask, what version of ubuntu are you using?

---

### Post by mc4man on 2008-12-27
If you really want it this is what you do
(note that 0.9.x can have issues, to revert just remove the packages and sources then reinstall vlc

Go into synaptic, search vlc and remove vlc, vlc-nox, libvlc0, and any vlc plugins

Then open System -> Administration -> software sources -> third party, click add. Add these 2 lines in _one at a time_
```

deb http://ppa.launchpad.net/c-korn/ubuntu hardy main
```

```

deb-src http://ppa.launchpad.net/c-korn/ubuntu hardy main
```

After adding click close, then reload. 
Now run

```
sudo apt-get install vlc
```

And you'll have 0.9.8a

---

### Post by CDiablo on 2008-12-27
Works thanks for the help guys.

---

