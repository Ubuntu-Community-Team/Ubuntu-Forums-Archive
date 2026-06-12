---
title: "libreoffice problem after installing Lubuntu 16.04"
date: 2016-08-24
forum: Multimedia Software
---

### Post by marioesposito859 on 2016-08-24
Hi,
I installed Lubuntu 16.04 with no problems.
But after installing libreoffice, the menu presents this problem:

[http://www.image-share.com/ijpg-3306-272.html](http://www.image-share.com/ijpg-3306-272.html)

How can I solve this problem?

Thank you
Regards

---

### Post by vasa1 on 2016-08-24
Please post the output of ```
dpkg --get-selections | grep libreoffice
```

---

### Post by ajgreeny on 2016-08-24
I presume your problem is that there is no menu showing?

Try renaming the hidden configuration folder ~/.config/libreoffice and try opening LO again as it may be a corrupt config file that is the problem.

---

### Post by vasa1 on 2016-08-24
> **ajgreeny said:**
> I presume your problem is that there is no menu showing?
...
The image OP linked to has File, Edit, View, Insert, etc (in Italian) overlapping (?) each other. I've included it here as a forum attachment.

I'm using LibreOffice in gtk2 mode and if I increase the font size in my gtk2 theme's *.gtkrc*, I can get the menu items to overlap as well.

---

### Post by ajgreeny on 2016-08-24
Thanks vasa1, I didn't notice that on the image the OP posted, and even if I had, I would not have realised what I was looking at.

It may still be worth renaming the .config/libreoffice folder as it seems likely it's a configuration problem, though as you say, it may be more the desktop gtk2 configuration than LO's own.

I run a version of LO from their PPA in my Xubuntu-14.04 and a recent update of that removed the libreoffice-gtk and libreoffice-gnome packages, changing some window appearances, though they did reappear in a later update.  Could be worth checking those gtk/gnome packages are installed and if not installing them now.

---

### Post by vasa1 on 2016-08-24
There's a lot going on with LibreOffice that makes things confusing!

Depending on the version, LibreOffice defaults to gtk3 mode if a high enough version of gtk3 is detected. A user on 14.04 who doesn't go the HWE route may still be on gtk 3.10 and so may not be able to use LibO's gtk3 even if so desired.

Users of 16.04 have gtk 3.18 and so, if they have a version of LibreOffice that defaults to gtk3, they'd need to take special steps to force gtk2 mode if they so desire.

A recent update of LibO seems to have junked *libreoffice-gtk* in favor of *libreoffice-gtk2*. According to [OMG Ubuntu]("http://www.omgubuntu.co.uk/2016/08/install-libreoffice-5-2-on-ubuntu-ppa"), one needs to remove *libreoffice-gtk* and to install *libreoffice-gtk2* instead (and maybe also *libreoffice-gnome*). I'm on 5.2 and haven't found the need to install *libreoffice-gnome* maybe because I'm staying with gtk2 mode.

---

### Post by ajgreeny on 2016-08-24
I just checked and had lo-gtk, lo-gtk2 and lo-gtk3 installed as well as lo-gnome;  The first of those was a transitional package and not needed so I have now removed that along with the lo-gnome that was uninstalled at the same time.

I'll report back if it changes the look of LO windows or of everything still looks as it did before removal of those packages.

EDIT:
No changes visible on 14.04 with those two packages removed, ie libreoffice-gtk and libreoffice-gnome.

---

