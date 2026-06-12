---
title: "GTK or Gnome..."
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by TenPlus1 on 2007-09-16
I love Gnome, it's a great window manager that's very easy to use and is pleasing to the eye...

..but.. wouldnt it be a lot easier if Ubuntu would standardize their packages on the live CD's and have GTK applications and utilities that dont hog space on the cd, so they can fit other *needed* items like ndiswrapper or gparted...

e.g.  EyeofGnome is a great picture viewer, but, gpicview is a hell of a lot smaller (28k instead of 2.2mb) and does the same thing only in GTK...

This way software loads quick (especially on the live cd) and can be replaced if the user really wants to install a gnome/kde/xfce version of their own...

---

### Post by por100pre1 on 2007-09-16
I think the Ubuntu Live CD is not intended to be used like an everyday use Live CD. Otherwise it would come with simple modules for saving user data in a hdd or media. You can make your own changes with [Reconstructor]("http://reconstructor.aperantis.com/"), I think.

---

### Post by K.Mandla on 2007-09-16
One of my long-standing complaints is the sheer bulk that comes with Gnome. So I generally build up from nothing and avoid anything that pulls in the least amount of Gnome stuff.

There are some fantastic GTK2 programs out there, so you just have to learn which ones are lean and which are too chubby to add. But as far as Ubuntu slicing off that fat for you ... I wouldn't look for it. 

Start tearing stuff out yourself, though. You have the right to choose what gets installed on your computer. ;)

---

### Post by TenPlus1 on 2007-09-16
I do actually un-install a lot of default software on Ubuntu, but there's always one's I cannot remove unless it takes off the whole gnome-desktop as well... ugg...

I just wanna see Ubuntu running as fast as it can on as little resources as possible...  That way it'll beat other distros for compactness, useability and stability...

---

### Post by K.Mandla on 2007-09-16
If you mean the ubuntu-desktop package, you can remove that safely, and then get at the stuff underneath it. 

ubuntu-desktop is just a metapackage, which is kind of like a bottlecap or a lable for all the stuff it includes. If you pull off that bottlecap, everything is fine underneath, you just don't have that nifty label for the whole list of packages and so forth.

So if you want ...

```
sudo apt-get remove ubuntu-desktop
```
And from there, the rest should pull away without any trouble. :)

---

