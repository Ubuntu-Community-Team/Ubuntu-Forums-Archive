---
title: "Graphic performance - any steps I can take?"
date: 2008-05-02
forum: Multimedia Software
---

### Post by ghope on 2008-05-02
I hope this doesn't seem too spineless, but I'm hoping that it is possible to get the graphic performance in 8.04 to match what I'm seeing in Win XP on the same machine (dual booting). 

After installing Hardy, I immediately noticed that scrolling through web pages seemed jerky/choppy. I booted into XP, visited the same pages and the scrolling was much smoother. Testing with the same page using my old laptop with 6.06 gave the same result, i.e., smoother scrolling than 8.04 on the newer desktop. 

Is this just a driver issue, or are there other steps I can take to get some improvement? Below are some details on my hardware. In both environments, the resolution and refresh rates were automatically set by the respective installers.

Controller: onboard Intel 82845G with 64MB VRAM
Resolution in Ubuntu: 1680x1050 @ 60Hz 
Resolution in Windows: 1280x720 @75Hz
Monitor: Samsung SyncMaster 2220wm

Many thanks for advice that anyone can share.
-Greg

---

### Post by scragar on 2008-05-02
You expect things to be as smooth when it's drawing more slower?

Either way, first thing I'd do would be to check for restricted drivers whenever there's a graphics problem, just because they work so much of the time( System>Administrattion>Hardware Drivers ), failing that make sure you havn't changed the zoom in firefox, firefox doesn't complain much at 10 or 20% zoom each way, but anything more and you start noticing that images/flash etc scroll at different rates to text, and the scroll bar moves on it;s own time altogether.

---

### Post by ghope on 2008-05-03
Thanks for the suggestions. I checked the zoom in FF and it's at zero (default). I also checked Hardware Drivers and none are listed.

I did visit the Intel website and found a driver for this graphic controller, but it's dated December 2004. Do you or anyone else following this thread have an opinion about me trying this in place of whatever current driver my system is using?

---

### Post by ghope on 2008-05-03
Update. I stumbled onto another post in which the writer said he had the Intel 845 chip and it was blacklisted by Compiz. So, I set System > Preferences > Appearance > Visual Effects to "none" and presto, graphics are peppy again!

I can live with this solution, but it would be nice to have some of the nifty effects without crippling the machine. If I want to achieve this, is my next step to install a more robust graphics card, and is there a hardward compatibility list somewhere that I could reference?

---

### Post by Enlitend on 2008-05-03
Here you go
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

hope it helps.

---

