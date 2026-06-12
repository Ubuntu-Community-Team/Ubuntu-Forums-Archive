---
title: "saving nvidia graphics card settings"
date: 2009-10-22
forum: Multimedia Software
---

### Post by K-Kariya on 2009-10-22
A while back I bought an nVidia GeForce 5200 PCI graphics card and finally got that thing to work on Ubuntu. My only problem now is that whenever I shut down, the settings never save and I always have to set my computer to twinview every time I log on(or leave it alone if i'm too lazy) Does anyone know about this issue or know anywhere to get more info on it??

---

### Post by lovinglinux on 2009-10-22
Try starting nvidia-settings as root and save it before quiting.

```
gksudo nvidia-settings
```

---

