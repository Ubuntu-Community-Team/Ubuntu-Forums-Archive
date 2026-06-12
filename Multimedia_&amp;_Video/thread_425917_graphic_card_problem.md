---
title: "graphic card problem"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by nitsthegame on 2007-04-28
i am unable to change the resolution of my screen using live cd of ubuntu 7.04

i am using the onboard graphic card of Intel DG965Ry

Even if i try to change the resolution it still does not changes.

Wht should i do?

---

### Post by musicinmybrain on 2007-04-28
I don't have that chipset, so I can't post any success stories, but:

[suggestion]("http://ubuntuforums.org/showpost.php?p=2058945&postcount=14")

[suggestion]("http://ubuntuforums.org/showthread.php?p=1646660")

---

### Post by RAKninja on 2007-04-28
any way to completely disable it? thats MY problem =\

---

### Post by musicinmybrain on 2007-04-28
> **RAKninja said:**
> any way to completely disable it? thats MY problem =\

I think that setting is usually in the BIOS. Maybe there's a way to do it in xorg.conf as well; I'd hesitate to make any suggestions I haven't tried.

---

### Post by RAKninja on 2007-04-28
changing the setting in bios makes ubuntu page fault crash before first command line interface is available. the listed fix for this (basically blacklisting the internal chip) does not seem to work for me.

---

### Post by nitsthegame on 2007-04-30
well how do u edit xorg.conf

whenever i try to open it in the terminal it says invalid command

---

### Post by musicinmybrain on 2007-04-30
First, make sure you have backed it up:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

This will allow you to restore your old configuration, since modifying your xorg.conf can easily stop you from booting into the graphical environment.

If you want to edit it in the graphical environment, use: ```
gksudo gedit /etc/X11/xorg.conf
``` If you want to edit it in the command-line environment (for example, because you broke your xorg.conf), use ```
sudo nano /etc/X11/xorg.conf
```

From there, you can make any changes: commenting out adapters you do not want to use, adding resolutions to the modelines, etc. Make sure to restart either the computer or just the X server (Ctrl + Alt + Backspace). Remember that you must restart just the X server on a LiveCD or your settings will be lost.

If you break it, use: ```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Commenting out the adapter you don't want to use may help you, RAKninja. I don't know what to tell you, nitsthegame. Whatever you do, don't forget to back it up first!

---

