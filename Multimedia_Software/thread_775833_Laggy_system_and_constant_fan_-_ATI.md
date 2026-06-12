---
title: "Laggy system and constant fan - ATI"
date: 2008-04-30
forum: Multimedia Software
---

### Post by insanealcoholicpenguin on 2008-04-30
ATI Radeon x850


When I enable the proprietary driver ubuntu suggests my system gets very laggy and my gfx fan runs full speed - even on an idle desktop.

I tried one from the package manager and the fan didn't seem to speed up but my system was super laggy and watching a video impossible.

Is anyone else having the same problem? (exactly the same issue when I tried the new mandriva too)

---

### Post by CarloMagno on 2008-04-30
Maybe you have the same problem I had when I upgraded from Gutsy to Hardy. For me the problem was that the driver was not used, in the Restricted Driver Manager it marked the "Ati proprietary driver" as "Enabled" but "Not in Use", I had to manually load it as suggested in post:
[http://ubuntuforums.org/showthread.php?p=4809394#post4809394](http://ubuntuforums.org/showthread.php?p=4809394#post4809394)

You have to enable it, it installs, asks for reinstall (probably you have already follow those steps), then load the driver (with the command in the post) and after a X session restart (CRTL+ALT+Backspace) everything was back to normal, at least for my system.

Hope that helps

---

### Post by CarloMagno on 2008-04-30
I forgot to mention that with this method you have to load the driver manually every time that you start the computer, so it is a bit of a nuisance if your system is not allways on.

If anyone knows how to permanently solve the problem I am eager to learn :-)

---

### Post by insanealcoholicpenguin on 2008-04-30
thanks for that! my driver was loaded but not 'enabled' this solves the lag problem but my fan still spins up at full speed for no apparent reason.

Would adding a different fan/heatsink do anything?


Looks like it's a bug in the driver....

[http://wiki.cchtml.com/index.php/Troubleshooting#Radeon_GPU_fan_is_very_loud_.2F_constantly_works](http://wiki.cchtml.com/index.php/Troubleshooting#Radeon_GPU_fan_is_very_loud_.2F_constantly_works)

> Radeon GPU fan is very loud / constantly works

    See bug 499 for additional information. 

It seems fglrx has a bug with all X800/X850 cards causing them to heat up excessively even when not in 3D mode. This behaviour will cause the cards' fans to function on full blast continuously. There is no known fix as of driver 8.31.05 or previous. Open source "radeon" driver does not exhibit this problem.

My Ati 1650GT has the same problem.It was normal when I enter ubuntu for 1 or 2minutes,and than ,the fan became crazy..No doubt it's because the temp~

It happens too with Radeon X1800 GTO and Radeon X1900 GT.

Possible solution (at least using a Mobility Radeon X1600): 

---

### Post by CarloMagno on 2008-05-06
I can't help with the fan, mine is working properly, not too much sound :-). 

After the last updates (four days ago) the fglrx driver and kernel was updated and now it loads automatically (not need to load it manually anymore), so if you haven't updated yet is a good time to try :-).

---

