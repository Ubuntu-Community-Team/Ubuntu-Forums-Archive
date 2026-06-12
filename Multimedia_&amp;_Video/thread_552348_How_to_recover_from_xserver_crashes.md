---
title: "How to recover from xserver crashes"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by swoosh on 2007-09-16
Hi,

This how to aims to help folks out there who have for some reason crashed xserver.

My personal experience was having a crashed xserver after my exploration with a planetarium software which apparently was not supported by my graphics card.

I am assuming you do not have graphical support now.

If you have a backup of xorg.conf then you will want to recover from it after login, do Part one.

If you do not have a backup of xorg.conf, then do not panick ! Do Part two.

**Part one:**

```
cd /etc/X11
```
```
sudo rm xorg.conf
```
```
sudo cp [location of your backed up xorg.conf] /etc/X11/
```
```
sudo shutdown -r now
```

If you have recovered you will see the normal GUI then good work! 

Please note you may have to enable your restricted driver via System/Administration/Restricted Drivers Manager if you have a compositing window manager installed.

**Part two:**

Now you will want to get a copy of the original xorg.conf. To do so, boot your system using the Live CD.

Once you have access to your system then,

Go to the location where you can make a copy of xorg.conf used by this temporary bootup to some permanent storage, restart your system and do Part one.

If you have recovered then thank yourself and remember to make a copy of xorg.conf. Good luck!

---

