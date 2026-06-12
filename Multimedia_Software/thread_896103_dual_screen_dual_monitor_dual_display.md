---
title: "dual screen/ dual monitor/ dual display"
date: 2008-08-20
forum: Multimedia Software
---

### Post by dazift on 2008-08-20
i have a compaq presario c700 (not sure what video card). i have not used a dual monitor setup with ubuntu b4 but I was wondering how it worked so i connected it to my desktop monitor and went into system/pref/screen resolution and i turned on the second monitor and pressed apply nothing changed, so i clicked clone output and that worked fine. i tryed many things after that to try to get the dual monitor thing happening but i couldent get it. am i forgetting something or do not have some settings setup or what am i doing wrong? thanks.

---

### Post by cdtech on 2008-08-20
Here's a post about dual monitors. It may help you get in the right direction.......
[http://ubuntuforums.org/showthread.php?t=463184](http://ubuntuforums.org/showthread.php?t=463184)

---

### Post by overdrank on 2008-08-20
moved :)

---

### Post by Jonniefive79 on 2008-08-21
This works for Nvidia cards... May be some way to get it to work with others IDK?

I found [_[COLOR="Blue"]this thread[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=1773584") much more helpful.  

No editing your xorg.conf

Basically you install the Nvidia Binary Drivers, see [_[COLOR="Blue"]this for help[/COLOR]_]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"), for my GPU (8600GT) I can either Install from synaptic Package Manager
1. nvidia-glx-new
2. nvidia settings

or use

```
sudo apt-get install nvidia-glx-new
```
and
```
sudo apt-get install nvidia-settings

```

Then just restart Xserver (ctrl-alt-Backspace) and run 

```
gksudo nvidia-settings
```

You should have a nice GUI for the Nvidia X Server Settings, which can also be found in System>Administration>Nvidia X Server Settings.

\\:D/\\:D/

---

### Post by anxiousdog on 2008-08-21
Jonniefive79: This worked for me! Thanks so much.

---

