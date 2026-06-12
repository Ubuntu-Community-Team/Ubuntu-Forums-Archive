---
title: "Roll back/reinstall Nvidia drivers from command line"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by nooozeguy on 2008-02-15
Hi,

I am having trouble with my system... When I boot into Ubuntu, the screen is unreadable... either the resolution is off or the wrong driver is being used.

I am hoping someone call help me either --from the command line-- reinstall the NVidia driver for a Radeon 9200 SE card or just roll back the driver to the default driver so that I can reinstall the correct driver from the GUI.

Thanks!

-Josh

---

### Post by benerivo on 2008-02-15
Try```
sudo nano /etc/X11/xorg.conf
```once you're in the file, use the arrow keys and Ctrl+X to exit. You want to find where it says Section "Device", and then change nvidia to nv

nv is the default driver that ubuntu uses for nvidia cards.

---

