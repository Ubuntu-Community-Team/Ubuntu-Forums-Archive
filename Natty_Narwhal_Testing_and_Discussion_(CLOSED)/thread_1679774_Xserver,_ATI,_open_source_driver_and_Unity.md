---
title: "Xserver, ATI, open source driver and Unity"
date: 2011-02-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-02-01
From this sticky thread:

[http://ubuntuforums.org/showthread.php?t=1675614](http://ubuntuforums.org/showthread.php?t=1675614)

>  Please keep an eye out for regressions in 3D functionality or
packaging issues associated with libdrm or mesa.I should shay sho. On my desktop, with:

```
02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
```I now cannot log in to Unity after some updates today. Only the classic desktop and no compiz. And I get a segfault error if I 'compiz --replace'. This is with the default open source driver with Unity/compiz hitherto working just fine since installation in December.

I'm not complaining. I just want to hear what other ATI users (with the open source driver) are experiencing before I break the install on my laptop with a Mobility Radeon HD4200. :|

On second thoughts, I'll leave off updating that one until I see what else filters through on my desktop. :)

---

### Post by dino99 on 2011-02-01
there is a lot of changes with X at time, so wait a few days (sorry i've not ATI and i dont use useless things)

---

### Post by ELD on 2011-02-01
Well for me on a HD 5770 i can't get Unity to work at all :(

Will the updated open source drives work with a HD5770 series?

---

### Post by lidex on 2011-02-01
Unity not working here after latest updates - using **nvidia** graphics. Compiz closing unexpectedly. All I get is desktop background. Classic works fine.

---

### Post by marijus on 2011-02-01
check out this thread: [http://ubuntuforums.org/showthread.php?t=1679795](http://ubuntuforums.org/showthread.php?t=1679795)

hope it works for you... if it does please also confirm bugreport

best, marijus

---

### Post by coffeecat on 2011-02-01
> **marijus said:**
> check out this thread: [http://ubuntuforums.org/showthread.php?t=1679795](http://ubuntuforums.org/showthread.php?t=1679795)

hope it works for you... if it does please also confirm bugreport

best, marijus

Thanks. It works. I've added the link in the other thread, but for others, libglew and libglewmx are in the g subdirectory of the repos, here:

[http://archive.ubuntu.com/ubuntu/pool/main/g/glew/](http://archive.ubuntu.com/ubuntu/pool/main/g/glew/)

I'll toddle over to Launchpad shortly.

---

