---
title: "[SOLVED] LightScribe and Linux."
date: 2008-05-13
forum: Multimedia Software
---

### Post by bilijoe on 2008-05-13
Dies anyone have any experience using LightScribe under Linux?  I went to their web site, and found they do have a Linux version of their software, so I downloaded and installed it.  Despite what seemed to be a clean install, it appears to have just disappeared into the ozone.  Does it act like a plug-in, and attach itself to available disk writing programs, or did it just vanish?:confused:

---

### Post by Magnes on 2008-05-13
I heard of LighScribe for Linux as a plugin for k3B but that was a long time ago.

---

### Post by iamnotthemessiah on 2008-05-14
im running lightscribe and its working really well. i just followed the instructions here [http://ubuntuforums.org/showpost.php?p=3838116&postcount=1](http://ubuntuforums.org/showpost.php?p=3838116&postcount=1)

if ur using 32 bit ubuntu just ignore the "--force-architecture" bit in the instructions

to add the lightscribe app to your applications menu just do as follows:
-rightclick on the applications menu (where it says applications/places/system)
-choose 'edit menus'
-choose the accessories menu on the left (or whatever menu u want it to appear in)
-in the right pane choose new item
-enter the folllowing
name:LaCie lightscribe (or what u want)
command:gksudo 4L-gui
comment: (leave blank)
optionally choose an icon by pressing the icon button on the left

voila
optionally launch it from a terminal: sudo 4L-gui

---

