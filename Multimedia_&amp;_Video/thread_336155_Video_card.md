---
title: "Video card"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by DapperMe17 on 2007-01-11
Hi,

Ubuntu Edgy...

I'm setting up an old P3, 600MHz HP desktop system, 384mb RAM, for a client. 

The stock graphics card is a 1999 Nvidia Riva TNT2 Vanta...8MB memory. It works great, except for video & audio playback, which is choppy, grainy & somewhat delayed.

I purchased a newer Nvidia MX4000...32mb memory. Hoping that the video/audio improves.    

Unfortunately, there was absolutely no improvement by using the newer, better card](*,) 


Am I running into a problem with the slow processor, or some sort of slow bus speed, etc???
GKrell does show "almost max" on the CPU usage when playing a video...94-98% CPU usage.

Thanks

---

### Post by taurus on 2007-01-11
Sounds like you need to install nVidia driver for your graphic card.  Here's a guide.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by DapperMe17 on 2007-01-11
Thanks Taurus,

I already have the nvidia-glx driver enabled from the repositories. I also have xorg/x11  edited to read "nvidia". 

Should I be using a different driver/config for the MX4000?

---

### Post by taurus on 2007-01-11
If you are using the one from the Repos, I _believe_ you are using the legacy driver!  You can go for the latest one for your new graphic card using that guide above.  You can remove the current driver with

Applications -> Accessories -> Terminal
```
sudo aptitude remove nvidia-glx
```

---

### Post by DapperMe17 on 2007-01-11
I'm a bit confused.

Right now, I'm set up with the nvidia-glx from the repositories. I modified the x11/xorg.conf file from "nv" to "nvidia" & added "1280x1024" to the resolutions.

All visuals are working fine & dandy as is, and I get the Nvidia startup screen as well. The only problem is the video playback. 



I tried everything in that guide, method #1....but got the xorg blue screen of death after uninstalling the nvidia-glx from repository. I had to recover by remodding the xorg.conf & reinstalling the nvidia-glx from repository.


I don't see the MX4000 in his "legacy" list, so I wouldn't think I would use that driver. 

Is there another driver I'm suppose to be updating to?

---

