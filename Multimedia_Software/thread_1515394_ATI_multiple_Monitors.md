---
title: "ATI multiple Monitors"
date: 2010-06-22
forum: Multimedia Software
---

### Post by chaosdesigner on 2010-06-22
Hey guys,

I know that there are quite a few Threads already on this subject, but I haven't found any help really on how to setup multiple monitors on Ubuntu 10.04 with my ATI Card. Basically I dont want to have the clone setup like I have it right now, but rather a different Desktop on my two screens. So like for example I already have 4 different Desktops and I would just find it extremely useful if I could have some programs run on one Screen while I do something else on the other.

I hope somebody can help me. You can find the name of my card in my signature. 

Thank you :).

---

### Post by Yellow Pasque on 2010-06-22
Back up your existing xorg.conf and generate a new one:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo aticonfig --initial -f --set-pcs-str="DDX,EnableRandR12,FALSE"
```
Log out to restart X server. If something goes wrong, press Ctrl+Alt+F1 to ge t to terminal (or boot to recovery mode) and restore your old xorg.conf.
```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

