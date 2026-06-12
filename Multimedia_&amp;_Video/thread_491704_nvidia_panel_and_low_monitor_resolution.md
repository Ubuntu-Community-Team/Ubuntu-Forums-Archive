---
title: "nvidia panel and low monitor resolution"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by rwallace1 on 2007-07-03
noob here, howdy

i can't seem to get access to the nvidia panel, "gksudo nvidia-settings" does not get a response in terminal

running dapper on a BioStar NF61S moboard, onboard GeForce 6100, Sempron

trying to get better than 1024 x 768 screen res, thought i'd try this before going into xorg

already went into the BIOS to look for more options, increased frame buffer size but have not tried to reconfigure yet

thanks

---

### Post by schtink on 2007-07-04
To the best of my knowledge, you can't change your screen resolution in the nvidia control panel.  You can, however, access Screen Resolution from the System > Preferences menu.

---

### Post by Gremlinzzz on 2007-07-04
Guide for the noob
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

---

### Post by LowSky on 2007-07-04
> **schtink said:**
> To the best of my knowledge, you can't change your screen resolution in the nvidia control panel.  You can, however, access Screen Resolution from the System > Preferences menu.

yes you can change it in the nvidia control panel


first log in as root
```
 sudo -i
```

then type

```
sudo nvidia-settings
```

 click apply, them remember to save the X Configuration file before quiting.

---

