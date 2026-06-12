---
title: "Nvidia X Server Settings"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by blockdude14 on 2007-03-20
I installed the nvidia driver but my screen resolution 1280X1024 works fine. When I pressed "apply" then "save to X configuration file" and restarted the computer it switched to default? I can't get it to stick on startup. :confused:

---

### Post by chewearn on 2007-03-21
I assumed you are referring to "save x configuration" button in nvidia-settings.  I think the problem is nvidia-settings don't have the permission to overwrite xorg.conf.  I workaround the problem by saving the file to home directory, then use
```
sudo cp xorg.conf /etc/X11/xorg.conf
```

---

### Post by fenian on 2007-03-21
From the terminal run...

> gksudo nvidia-settings

this will run nvidia-settings as root and allow you to save changes to the xorg file.

---

