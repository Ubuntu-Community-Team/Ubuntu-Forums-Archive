---
title: "new brushes in GIMP"
date: 2017-11-19
forum: Multimedia Software
---

### Post by andysharpie on 2017-11-19
I recently downloaded some additional brushes for GIMP, but haven't figured out how to integrate them into the application. Can anyone help me out?

---

### Post by coffeecat on 2017-11-20
Originally posted in the Art & Design sub-forum whose tagline states, *"Discuss various aspects of Ubuntu and Art here. Questions about using software for image editing should go in the Multimedia Software section."*

*Thread moved to **Multimedia Software.***

---

### Post by Holger_Gehrke on 2017-11-21
If GIMP is installed correctly and you've run it before, there's a hidden directory '.gimp-'+version (example: gimp-2.8) in your home directory, that contains a directory 'brushes'. Just put the brushes in there and they'll be loaded the next time you start GIMP. If GIMP is already running while you do this, you can right click in the brushes dialog and choose 'reload' from the menu.

Holger

---

### Post by andysharpie on 2017-11-22
I found the gimp directory, but when I attempt to move the files I get an "Error while moving" message. When I clicked the "show more details" on the error message, it said "permission denied." Does this mean that I need to be root to accomplish this?

---

### Post by Holger_Gehrke on 2017-11-22
What directory are you trying to move the brush-files to ? '/usr/share/gimp/2.0/brushes/'  is a system wide data directory for all user's and only writeable for root. Each user also has a gimp data, configuration and plugin directory in his home directory. This directory has a name starting with a dot '.' and isn't normally shown in the file manager for this reason. It should be writeable for you (and no other user except root). You have to tell your file manager to show hidden files. On Thunar (the file manager of XUbuntu / XFCE, which I'm using) the key combination 'ctrl-h' or the option 'show hidden files' in the view-menu does this. I think for Nautilus - the file manager of Gnome, which you probably have, since it's the default on Ubuntu - the key combination should be the same. If you're using something else, I can't tell you how to show hidden files and directories.

Holger

---

### Post by andysharpie on 2017-11-22
Yes, I do have the Nautilus file manager, and yes, I was trying to to move the files into /usr/share/gimp/2.0/brushes/, which was the problem. I did have to run a file extraction for GIMP to read the new brushes, but after that they ran perfectly fine in the .gimp-2.8 directory. Thanks so much!

---

