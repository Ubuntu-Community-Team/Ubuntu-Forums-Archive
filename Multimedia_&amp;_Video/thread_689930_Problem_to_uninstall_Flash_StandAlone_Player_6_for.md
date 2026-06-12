---
title: "Problem to uninstall Flash StandAlone Player 6 for Linux"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by crdrews on 2008-02-06
Hi!

I have installed the Flash StandAlone Player 6 for Linux from Adobe's website. The player didn't work for me (missing library that I coulnd't find) and so I decide to use swiftweasel to watch flash animations off-line.

The problem is that I can't uninstall the flash player SA! 
During the installation, that I have done as root with the command # su -s , I told it to put a link at my desktop.

So I uninstall it following the procedures at the readme.txt that come with it, but everytime I reset my computer, a Link to .gnome-desktop is created in my workspace with a link to flash player inside.

How can I make it stop?

A.: just need to erase .gnome-desktop here.

---

### Post by wolfen69 on 2008-02-07
```
sudo nautilus
```
then navigate to .gnome-desktop and delete.

---

