---
title: "Installed 11.04 but have gnome instead of unity!!! :("
date: 2011-02-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by godfromdfo on 2011-02-20
I upgraded from 10.10 and still have gnome but I want to use unity :( help me please pro linuxers!!!

---

### Post by PaulW2U on 2011-02-20
> **godfromdfo said:**
> I upgraded from 10.10 and still have gnome but I want to use unity :( 
Try this, log out but before logging back in click on your username. A menu should appear in the botton panel. Is there one that says "Ubuntu Desktop Edition" or similar? Choose that one and log back in.

By the way all Natty posts should go in the appropriate forum:

[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

I'm sure this thread will be moved there shortly. ;)

---

### Post by s.fox on 2011-02-20
Thread moved to  Natty Narwhal Testing and Discussion

---

### Post by godfromdfo on 2011-02-20
> **PaulW2U said:**
> Try this, log out but before logging back in click on your username. A menu should appear in the botton panel. Is there one that says "Ubuntu Desktop Edition" or similar? Choose that one and log back in.

By the way all Natty posts should go in the appropriate forum:

[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

I'm sure this thread will be moved there shortly. ;)

Oops, sorry for wrong section.

Yes, it says classic (when I click on it, it loads gnome) ubuntu desktop edition loads a screen that looks like gnome but doesn't have any panels, however if I do gnome-panel in a terminal it shows the panel and looks like gnome..

---

### Post by godfromdfo on 2011-02-20
Picture if it helps - this is ubuntu desktop edition with which had no panels working at first so I opened a terminal and used gnome-panel

---

### Post by cariboo on 2011-02-20
What graphics card does your system use?

---

### Post by godfromdfo on 2011-02-20
> **cariboo907 said:**
> What graphics card does your system use?

It uses a nvidia 9400GT, which brings me to a little story about when I first installed Natty

When I first installed it I went to Additional Drivers to install a GPU driver and it had 3 diffrent drivers to choose from, I chose the first one which was called Nvidia Xorg binary driver, rebooted and it started up as a black screen so I had to write something like sudo install x (sorry I can't recall whole command) and then it was ok and I thought hmm, let's try the second driver which had the same name as the 1st but a slightly diffrent description - same thing happened. Got back into ubuntu and tried the 3rd and final driver (experimental support for nvidia) and what do you know, it worked kinda, but it's had alot of problems compared to 10.10 such as no "effects" menu under right click desktop anymore, the resolution is quite bad (8xx/6xx or 12xx/9xx) Hope that helps :D

---

### Post by Harry33 on 2011-02-20
> **godfromdfo said:**
> It uses a nvidia 9400GT, which brings me to a little story about when I first installed Natty

When I first installed it I went to Additional Drivers to install a GPU driver and it had 3 diffrent drivers to choose from, I chose the first one which was called Nvidia Xorg binary driver, rebooted and it started up as a black screen so I had to write something like sudo install x (sorry I can't recall whole command) and then it was ok and I thought hmm, let's try the second driver which had the same name as the 1st but a slightly diffrent description - same thing happened. Got back into ubuntu and tried the 3rd and final driver (experimental support for nvidia) and what do you know, it worked kinda, but it's had alot of problems compared to 10.10 such as no "effects" menu under right click desktop anymore, the resolution is quite bad (8xx/6xx or 12xx/9xx) Hope that helps :D

In this Development Forum there are a lot of threads about Natty and NVidia proprietary drivers.
For full and smooth 3D environment you need to have NVidia proprietary drivers installed (package nvidia-current).
But at the moment these drivers do not support the latest development version of xserver (1.10).
Either you have to downgrade the xserver to series 1.9 or you have to wait until NVidia Corp releases new drivers supporting xserver 1.10.

You are not alone with this problem.
It is just that it should be more clearly emphasized, that development versions of Ubuntu are not actually for beginners.

---

### Post by godfromdfo on 2011-02-20
> **Harry33 said:**
> 
You are not alone with this problem.
It is just that it should be more clearly emphasized, that development versions of Ubuntu are not actually for beginners.

This.

Your quote is so true, I saw some youtube vid saying ubuntu 11.04 and it took me to ubuntu's website and it didn't really mention it wasn't for new users.. oh well, might as well stick with it til it goes mainstream :D

mind explaining how I downgrade to 1.09? thanks

---

### Post by Harry33 on 2011-02-20
> **godfromdfo said:**
> This.

Your quote is so true, I saw some youtube vid saying ubuntu 11.04 and it took me to ubuntu's website and it didn't really mention it wasn't for new users.. oh well, might as well stick with it til it goes mainstream :D

mind explaining how I downgrade to 1.09? thanks

Here is some more info on this subject.
[http://ubuntuforums.org/showpost.php?p=10475706&postcount=153](http://ubuntuforums.org/showpost.php?p=10475706&postcount=153)

---

### Post by cariboo on 2011-02-20
I installed the daily build yesterday on a system in my shop, it is running a 9400GT, I manually installed libgl1-mesa-dri-experimental via synaptic, on reboot, I had the Unity desktop, although using the applications menu in the panel caused an immediate lockup. The one thing that wasn't right though was theming, app-indicator icons were wrong, and icons in the panel were wrong too.

---

### Post by godfromdfo on 2011-02-20
> **cariboo907 said:**
> I installed the daily build yesterday on a system in my shop, it is running a 9400GT, I manually installed libgl1-mesa-dri-experimental via synaptic, on reboot, I had the Unity desktop, although using the applications menu in the panel caused an immediate lockup. The one thing that wasn't right though was theming, app-indicator icons were wrong, and icons in the panel were wrong too.


Are you suggesting I install libgl1-mesa-dri-experimental? or are you saying don't because there are lockups under apps menu? thanks :D

---

### Post by cariboo on 2011-02-20
Yes I am suggesting you install libgl1-mesa-dri-experimental. My system locked up and I haven't taken the time to troubleshoot the problem yet.

---

