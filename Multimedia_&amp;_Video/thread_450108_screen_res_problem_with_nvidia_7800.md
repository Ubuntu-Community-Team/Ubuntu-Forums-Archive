---
title: "screen res problem with nvidia 7800"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by mandarke on 2007-05-21
just installed ubuntu 7.04 and all seems well. however, i am limited to running at 1024x768 @ 58Hz. surely this is not normal.

gfx card - BFG NVIDIA GeForce 7800 GS OC 256MB AGP
processor - intel p4

i am using the nvidia drivers that came with ubuntu 7.04

---

### Post by spin2cool on 2007-05-21
You'll need to edit your /etc/X11/xorg.conf file.

1) make a backup of the file (cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup)

2) edit the file (sudo gedit /etc/X11/xorg.conf)

3) It should be pretty easy to see where to add additional resolutions.  It'll look something like this:
```
Modes      "1280x1024" "1024x768" "800x600" "640x480"
```

Add your preferred resolution to the beginning of the list

---

