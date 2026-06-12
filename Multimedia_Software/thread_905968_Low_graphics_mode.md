---
title: "Low graphics mode"
date: 2008-08-30
forum: Multimedia Software
---

### Post by chroncile on 2008-08-30
Please help me, I've tried everything, but I cannot fix it. 
I did something once, and the low graphics mode didn't appear, but when I tried glxgears, it didn't work so I know somethings wrong.

Oh, I also did an upgrade to hardy.

Thanks. :D

---

### Post by wolfen69 on 2008-08-31
in the future, you might want to consider doing a fresh install instead of upgrading. in the meantime, try```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x by ctrl-alt-bksp.

---

### Post by chroncile on 2008-09-05
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080905161223
```
:(

---

### Post by wolfen69 on 2008-09-05
that's what it's supposed to do. after you run the code i gave you, do ctrl-alt-bksp.

---

### Post by ratmandall on 2008-09-05
I have the same problem as him, the terminal command didn't work for me, last thing I did in ubuntu was ```
shutdown 1
``` 
in the terminal,
then when I booted up the next day it was in low graphics mode I don't know what to do I've tried editing xorg.conf with my screens refresh rates but to no avail:confused:

---

### Post by ratmandall on 2008-09-06
Sorry to post in your thread but Im also getting this error on startup

kinit:no resume image, doing normal boot

---

### Post by chroncile on 2008-09-06
Thanks for the reply, I did that and it worked, but I have no video drivers. I have a nvidia geforce 6600, I went to hardware drivers, but it "No proprietary drivers are in use on this system"

---

### Post by Qloor on 2008-09-06
> **chroncile said:**
> Thanks for the reply, I did that and it worked, but I have no video drivers. I have a nvidia geforce 6600, I went to hardware drivers, but it "No proprietary drivers are in use on this system"

Try this guide: [http://wp.uberdose.com/2004/12/11/ubuntu-and-nvidia-geforce-6600/](http://wp.uberdose.com/2004/12/11/ubuntu-and-nvidia-geforce-6600/).

---

### Post by chroncile on 2008-09-07
Thanks for you reply, but I already figured it out. I uninstalled every video driver I had, and then installed the one from nvidia.com, works way better then the regular ubuntu default, I went from 2700 fps in glxgears to 5000 fps :D

---

