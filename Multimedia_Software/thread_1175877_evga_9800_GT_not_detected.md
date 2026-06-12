---
title: "evga 9800 GT not detected"
date: 2009-06-01
forum: Multimedia Software
---

### Post by fyaskoxc on 2009-06-01
Hey guys,
i just switched from xp to hardy heron, since i loveee linux so much :]
anyways, so i'm having a problem. I have the 9800 GT installed but i need the drivers. 
When i go to "Hardware Drivers" it says that
No proprietary drivers are in use on this system
so i manually downloaded the driver from the website and did
sudo sh "driver's name"
i also did 
sudo chmod +x "driver's name" 
and none of them work 

they come out with
sh: Can't open NVIDIA-Linux-x86-180.60-pkg1.run

i also looked up envy and saw that there isn't a version for hardy heron. 
Help me, i wanna use compiz so bad. :/

---

### Post by tactx on 2009-06-01
Envyng works well with hardy...

```
sudo apt-get install envyng-qt
```

use 173 driver. In hardy this worked better for me than the NVIDIA site drivers.

If you want to run the NVIDIA drivers make shure meet these conditions:

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

also after you down load the drivers pkg move it to your home dir and check the "execute as application" box under properties.

---

