---
title: "Install nVidia &amp; ATI Drivers Together (have both cards)"
date: 2008-08-07
forum: Multimedia Software
---

### Post by awells527 on 2008-08-07
I am attempting to use an ATI card together with an nVidia card using both binary drivers.  Is this possible?  When I have both cards active, both drivers appear in the Restricted Drivers window, but when I check one, it removes the other.  It appears that there is a package conflict between the two.  The cards are:

nVidia GeForce 8600 GTS (PCI Express)
ATI Radeon HD 3200 (onboard)

Thanks for any assistance :)

---

### Post by awells527 on 2008-08-07
bump

---

### Post by Forlornity on 2008-08-07
May I enquire as to whether you have attempted to use envy?
Run:
sudo apt-get install envyng-gtk
in a terminal then, once it is complete, run:
envyng -g
and see if you can get anywhere.

- Forlornity

---

### Post by awells527 on 2008-08-07
Hi, thanks for your response.  I have tried envy.  The driver packages in apt-get conflict with each other, so even if I run 'sudo apt-get install nvidia-glx-new' manually, it removes ati's binary driver.

Is there a way to force the package manager to install packages that aren't meant to be installed together?

---

### Post by markbuntu on 2008-08-08
You are probably going to have to manually install the drivers and then make extensive changes to your xorg.conf so they can be used. Multiple device sections and screen sections will be necessary as each driver and the screesn they drive will need separate ones. A guy in this thread has 4 video cards. His xorg.conf is in there somewhere. It is a place to start.

[http://ubuntuforums.org/showthread.php?t=854719](http://ubuntuforums.org/showthread.php?t=854719)

Of course if they call for loading modules that conflict, this can break the kernel or the x server among other things. I hope you don't really really need this machine you are doing this to.

---

### Post by awells527 on 2008-08-08
Sweet, I will look at that thread.  I am ok with manually installing drivers if the package manager is going to give me problems.  I kinda wish this would support it out of the box though.

> I hope you don't really really need this machine you are doing this to.

Yeah...it is.  If I have to do things that aren't easilly undone, then I might throw in another hard drive and run it on a test installation.  I wish this was something I could tinker with on a virtual machine or test box. :(

---

