---
title: "x800 issues"
date: 2006-03-07
forum: Multimedia &amp; Video
---

### Post by erakepio on 2006-03-07
installed ubuntu smoothly and got all the packages down i needed and set up my network connection.  Next i needed to sort my gfx car dout.  Itwas running in a 1024-768 resolution where I used 1280-1024 with Suse.

I downlaoded the ATi Linux drivers from the net and followed their install, rebooted..no success.  So i decided to follow the tutorial [here]("http://ubuntuforums.org/showpost.php?p=423584") which didnt seem to correct the problem as now wheni reboot xserver wont start at all and im left with a shell.  re-installed and followed the guide again but the same happened.  

Not sure really what I can try next.

---

### Post by Teroedni on 2006-03-07
You can use [COLOR="Blue"]driver "radeon"[/COLOR]
But the your left with only 2d :/

If you wanna have 3D as well
use this howtoo
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

Follow this howtoo and if you still have problems come back here and copy the text from these 2 commands

```
sudo gedit  /etc/X11/xorg.conf
```

```
sudo gedit /var/log/Xorg.0.log
```

---

