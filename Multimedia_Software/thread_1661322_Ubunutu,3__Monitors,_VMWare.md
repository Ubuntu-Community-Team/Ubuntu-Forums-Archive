---
title: "Ubunutu,3  Monitors, VMWare"
date: 2011-01-06
forum: Multimedia Software
---

### Post by KenBeanNet on 2011-01-06
Hey guys.  

I am using a ATI 3500 HD Radeon card with the latest 10.12 drivers.  I can install fine, and set up all 3 monitors with the control panel.  Once I turn on Xinerama, I can no longer enter the control panel without a crash.  But that really isn't an issue as everything is set up and works fine.  Once I load into VMware and run it, about 10 minutes in, it just crashes.  The computer still responds to ALT CTRL DEL but it must be restarted.  I see that 3D acceleration in the past caused issues. 

Is this still the case?

Also, I tried to apply the PPA fix that people have been using here : [https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539]("https://launchpad.net/%7Ejared-bunting/+archive/xorg-xserver-650539") and now my computer will not boot.  It simply black screens once I try to boot.  Any suggestions to fix this?  I can re-install but it would just take 4 hours to install Ubuntu + VMWare + all programs.  Is there a way to get into the terminal with 10.10?  

Thanks for any insights people may have.

---

### Post by KenBeanNet on 2011-01-06
Ok.  So this is what I did.  Go to Package Manager > Settings   > Repositories

Go to updates tab, "Pre-released updated (Maverick-proposed)"

Hit reload, do updates, reboot.

Then in VMWare turn off 3D acceleration.  


I haven't crashed since with 3 monitors.

---

