---
title: "[SOLVED] Nvidia X server settings ... :S"
date: 2008-07-07
forum: Multimedia Software
---

### Post by shaheel16 on 2008-07-07
Well Im on ubuntu 8.04 Ed. and im trying to configure tv out for my graphics card.. (nvidia GF 4 Mx 4000) . Tv out works well from booting up to ubuntu showing login window. then i get a black screen.


I have installed nvidia settings. But when i enable my tv out with a separate x session im not being able to save the configuration file..im having the following error..:

"Unable to create new X Config backup file '/etc/X11/xorg.conf.backup'  "


Any help here plzz...:confused:

---

### Post by Marshal0505 on 2008-07-07
> **shaheel16 said:**
> Well Im on ubuntu 8.04 Ed. and im trying to configure tv out for my graphics card.. (nvidia GF 4 Mx 4000) . Tv out works well from booting up to ubuntu showing login window. then i get a black screen.


I have installed nvidia settings. But when i enable my tv out with a separate x session im not being able to save the configuration file..im having the following error..:

"Unable to create new X Config backup file '/etc/X11/xorg.conf.backup'  "


Any help here plzz...:confused:

try opening nvidia-settings as root , that should fix it.

```
gksu nvidia-settings
```

---

### Post by shaheel16 on 2008-07-07
yep.. now it saves successfully... thanks... Hmmm dont know yet if its working.. Got to restart... :p

---

### Post by shaheel16 on 2008-07-07
YES YES YES YES!!!!!! Its work! TV out under Ubuntu... Wowwww... Thanks Marshal0505 :popcorn::KS:)

---

