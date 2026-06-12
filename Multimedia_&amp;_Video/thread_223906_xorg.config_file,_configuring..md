---
title: "xorg.config file, configuring."
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by Stephen_A on 2006-07-27
I've just installed Ubuntu on a Dell 1100. The video display is in a square in the middle of the screen. Someone advised me to adjust VertRefresh, HorizSync and "Modes" in the etc/x11/xorg.config file.
  I've found this file but I can't find Vertrefresh or HorizSync in the file. If I do, how do I adjust them?
  Also, the text editor only opens the files as 'read only.' How do I adjust it so I can open the files to edit?
  Many thanks in advance. 

Stephen.

---

### Post by stimpsonjcat on 2006-07-27
before editing the file by hand, try ```
sudo dpkg-reconfigure xserver-xorg
```
I think that your problem has more to do with wrong resolution settings than refresh rates though. try to find out your monitor's native resolution and adjust your x server accordingly.

if you want to edit files that belong to the root user, you have to type sudo gedit first. in your case that would be
```
sudo gedit /etc/X11/xorg.conf
```
in any case, be sure to make a backup copy of it first in case you mess up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Further information can be found in the [ubuntu desktop guide]("https://help.ubuntu.com/ubuntu/desktopguide/C/index.html") and the [wiki]("https://help.ubuntu.com/community/UserDocumentation"):
[https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html")
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by tseliot on 2006-07-27
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

### Post by Stephen_A on 2006-07-27
Thanks for all your suggestions. I will try that guide. It looks very comprehensive.

---

