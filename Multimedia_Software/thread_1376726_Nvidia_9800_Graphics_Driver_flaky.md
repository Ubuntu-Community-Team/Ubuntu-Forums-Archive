---
title: "Nvidia 9800 Graphics Driver flaky"
date: 2010-01-09
forum: Multimedia Software
---

### Post by hummvee2134 on 2010-01-09
Hey everyone. 

I just installed ubuntu 9.10 on my computer ( i went cold turkey from windows) but i cant help but notice how flaky the graphics driver is. For example, while watching a movie full screen, and theres a lot of action on the screen, i get these horizontal lines and a bit of choppyness.

I first tried the driver in the package manager, then the driver from nvidia's site. They both seem the same.

Is there something im missing? do nvidia drivers just suck for linux?


Note:

Graphics Card:nvidia 9800gt 
Driver version: 190.53
Ubuntu install: x64 9.10

If you need any more information please let me know.

Thank you very much.

---

### Post by tsucol11 on 2010-01-09
Did you get the Nvidia drivers from the Ubuntu download section or the Nvidia site?

I am running Ubuntu 9.04 64 bit with Nvidia 9800GT card using latest drivers on the Ubuntu site ver 180....

Running movies full screen just fine.

Brian

> **hummvee2134 said:**
> Hey everyone. 

I just installed ubuntu 9.10 on my computer ( i went cold turkey from windows) but i cant help but notice how flaky the graphics driver is. For example, while watching a movie full screen, and theres a lot of action on the screen, i get these horizontal lines and a bit of choppyness.

I first tried the driver in the package manager, then the driver from nvidia's site. They both seem the same.

Is there something im missing? do nvidia drivers just suck for linux?


Note:

Graphics Card:nvidia 9800gt 
Driver version: 190.53
Ubuntu install: x64 9.10

If you need any more information please let me know.

Thank you very much.

---

### Post by hummvee2134 on 2010-01-09
ive used both. i just downgraded from ver 190 to ver 185.18.36

Which graphics driver version are you using?

190 i got from the nvidia site. 185 i got from the ubuntu download.

---

### Post by rand()m on 2010-01-09
Which media player are you viewing the movie in?

---

### Post by hummvee2134 on 2010-01-09
vlc. the problem doesn't happen in only movies. but movies are where it can get really annoying .

I attached a screenshot of the problem happening with compiz.

---

### Post by rand()m on 2010-01-09
That's a V-sync problem.

---

### Post by hummvee2134 on 2010-01-09
How do you fix it?

---

### Post by lopita on 2010-01-09
```
sudo aptitude install ccsm
```

Then go to System>>Preferences>>CompizConfig Settings Manager, then click General Options (in the general section), click the Display Settings tab (2nd from left) and check/tick Sync To VBlank.

---

### Post by hummvee2134 on 2010-01-09
no kidding, that was easy.

Thanks for the help guys, appreciate it.

---

### Post by lopita on 2010-01-09
You're welcome.

---

