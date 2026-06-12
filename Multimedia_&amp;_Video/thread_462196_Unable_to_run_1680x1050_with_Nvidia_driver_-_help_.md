---
title: "Unable to run 1680x1050 with Nvidia driver - help? :("
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by TS28 on 2007-06-02
After going into "Sytem -  Administration - restricted driver manager", then enabling the Nvidia driver, I am still not able to run my monitor (Dell 2007 wfp) in 1680x1050.

My video card is an EVGA Geforce 7950GT 

I know that at one point, my girlfriends brother (Linux wiz) was able to get my Ubuntu installation to where I am able to access an actual Nvidia panel with lots of cool stuff, one of them giving me the ability to change that as my resolution, even though "System - preferences - desktop resolution" wasn't able to.  Unfortunately, this is a new install of Ubuntu, and I am having trouble accomplishing what he had done :(

Thanks a ton for reading :)

-Stefan

---

### Post by solarwind on 2007-06-02
Try typing nvidia-settings in the terminal to get the nVidia settings panel. Then select the appropriate resolution from that panel.

---

### Post by TS28 on 2007-06-02
Hooray, it worked!  Many thanks! :D :D :D :D :D

---

### Post by tseliot on 2007-06-02
and if the resolution changes on next reboot you will have to type:
```
sudo nvidia-settings
```

and save your settings from there

---

### Post by TS28 on 2007-06-03
Wow, thank you tseliot.  I had exactly that problem, and whenever I would try to change to 1680x1050, it would completely crash.  I applied what you said and working beautifully.

You people are amazing.

---

### Post by Moosetek13 on 2007-06-03
1680x1050 is cool - especially with Beryl.

---

### Post by em3raldxiii on 2008-01-03
> **tseliot said:**
> and if the resolution changes on next reboot you will have to type:
```
sudo nvidia-settings
```and save your settings from there


I am having even more trouble with the same thing.  For some reason, 1680x1050 does not show up in my nvidia-settings menu; I only have 1600x1200 and 1600x1024.  I have tried editing my xorg.conf file with rather mixed bad results.  In many situations, I get "Out Of Range" errors on my monitor.  I have tried using the configuration editor as well, with no effects.

Also, if I try to access my tty1-6, I get the same out of range problem.

Fresh Ubuntu 7.10 install, with restricted driver installed.  Geforce FX5600GT.  Viewsonic vx2240w (22 inch widescreen 2ms latency) with 1680x1050 being my native resolution.  1600x1024 looks okay, but obviously not as crisp as the correct res would be.

Help would be greatly appreciated!!

---

