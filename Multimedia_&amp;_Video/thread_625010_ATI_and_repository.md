---
title: "ATI and repository"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by rcmn on 2007-11-27
source 
[http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_711_linux.html](http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_711_linux.html)
AMD Catalyst&#8482; Linux 7.11 (new 8.4xxx. renamed to match the win$ driver))
AMD recommends that this release of the AMD Catalyst&#8482; Linux software driver not be used for distribution packages. Distributors should continue to use the AMD Catalyst&#8482; Linux driver version 8.40.4

So why do we still have the 8.37 in the repository for Gusty???:confused:

---

### Post by nzadLithium on 2007-11-27
takes time to get the updated versions into the repository and also some people consider the new drivers to be 3rd stage alpha drivers from amd. So they might be deemed not stable enough to put in repositories? Just follow the gutsy install guides for the amd drivers you should be able to install it easy enough from one of them. Its really just a cut and paste commands job :D

---

### Post by rcmn on 2007-11-27
Well i have been trying every single howto that exist with almost every new version for the past 2 years. And well ... the best install/stability/result is the "default proprio" from the repository. I have a 9800 pro with kubuntu and that's my curse. But with AMD stating that i was hoping 8.40 was stable enought.

---

### Post by nzadLithium on 2007-11-27
just install it following this 
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
do method 2.
its what i did but if you want to use the new catalyst drivers then I think you have to have gutsy coz they dont work in feisty (unless i did something really wrong) they get you good 2d accel but none of the opengl libs are installed so theres no 3d accell while using feisty.

---

### Post by rcmn on 2007-11-28
i have gusty .i did try methode2 many time with feisty and gusty with various version of the driver, 
the worst was the tool called envy,i could not get X to come back and i had to reinstall.happened with feisty and gusty. the usual break is black screen or mesa.an the fix is to log into the recovery console and fix xorg,conf/unload modules/etc...but with envy nothing worked LOL. broken for good!
maybe better for nvidia.
Anyway at this point i don't want to risk anything i can't afford to spare more time experimenting.
right now i have 3d accel and i can kinda play at ETQW but there is some serious texture issues,example i cannot see the body of the human just the weapon,So i see floating weapon ,Or i can't see certain vehicles unless i run into them,etc...

---

### Post by nzadLithium on 2007-11-28
i doubt amd will have fixed issues like that this quickly. It may be better to just wait for the ubuntu repositories to be updated. Once they are in the repositiories it means they should work without trouble so since you cant afford to have anything screwed up i would just wait. 

With ETQW have you tried searching google for you problem and see if anyones found a game specific fix? or maybe you could play around with gfx settings in game and see if anything in there will bring the game models up properly.

---

### Post by rcmn on 2007-11-28
yep i came about the same conclusion.That's why i'm impatient to see new driver in the repo.
I did also search for fix regarding this problem .And each time i had the "...install the newest ATI driver..." .
So i guess i will just wait...

---

### Post by Vajk on 2007-12-07
I hope that the repos update will happen sometime soon. I have a Mobility Radeon X300 in an Inspiron 9300. My experience is also that the drivers in the repos are the most easy to install. I can't find some packages which are required to work the ati driver properly. After I followed the guide from ATI's website AtiCatalyst controller still not starts and I have no 3D.

---

