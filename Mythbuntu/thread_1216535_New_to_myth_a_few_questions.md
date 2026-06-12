---
title: "New to myth a few questions"
date: 2009-07-18
forum: Mythbuntu
---

### Post by Drobbins on 2009-07-18
Hey Everyone. 

I have recently decided to install mythbuntu been using ubuntu for some time but i have some questions;

I have a external hard drive that has all my movies on how do i tell myth they are on their?
How do i move to the terminal
How do you do updates - update manager dosent appear on it's own

Cheers
Rich

---

### Post by crez79 on 2009-07-18
Mythvideo is a plugin for mythtv that organizes and plays videos. If it isn't installed, you can use the mythbuntu-control-centre to install it. Then you configure it from within mythfrontend under media settings. First you must make sure that the hard drive is mounted, there are a bunch of howto's that can explain how to do this in detail.

To use terminal you can open it from the applications menu bar or hit alt-f2 and type either, "xterm" or "xfce-terminal" or "gnome-terminal" depending on if you are using gnome or xfce.

For updates, type ```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
``` into terminal and on the updates tab, you can configure the update-manager's behavior.

---

