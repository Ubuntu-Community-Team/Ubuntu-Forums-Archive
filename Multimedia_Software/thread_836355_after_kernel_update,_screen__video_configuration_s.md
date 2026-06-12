---
title: "after kernel update, screen / video configuration screws up"
date: 2008-06-21
forum: Multimedia Software
---

### Post by hurinth on 2008-06-21
Hi. Originally I used Envy to install nvidia drivers and it works ok. Now there is  new driver release not cover yet by Envy, so I learned how to install it to a fresh Ubuntu installation:> sudo /etc/X11/gdm stop
sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run (I click yes to everything except support for 32bit libraries)
sudo /etc/X11/gdm start
This works great as the drivers are very stable by themselves

THE PROBLEM:
Every time there is a new kernel to update with, my drivers get completely screwed.
I know this beforehand, the problem is I still can't reinstall the drivers successfully

Symptoms:
After kernel update and sys reboot, I get a login windows at vga resolution or worse. When I log in the nvidia xserver settings application is still available under Applications>System, but if I click there I get that the drivers are not in use (u bet...800x600 clarifies everything)

TROUBLESHOOTING:
If I try to install the drivers again, I still get low resolutions but the advance desktop settings work, like the cube, my emerald theme, wobbly windows, all but a decent resolution...

I copied all the text from the first xorg.conf.backup to the xorg.conf and still nothing. At this point if I reboot, I will loose usage of the drivers and the system will come up without them, so advance desktop setting wont work, neither emerald theme.

I installed Envy just to have the driver uninstalled but get no positive result.

So my question would be: How can I install the drivers after a kernel update and successfully get the appropriate resolution (1680x1050) and not loosing the drivers after a reboot?

Thanks all

Asus VW2202 22" LCD
Asus Crosshair mobo
Kingston hyperx 2x1GB DIMMs
EVGA 8800Gts 320MB
AMD 5600 X2

---

### Post by hurinth on 2008-06-21
SOLVED!

Great! I didn't know this command:
> sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart

I found that dpkg-reconfigure reverts the configuration files of a specific package to the initial standard configuration for the package xserver-xorg. -phigh is supposed to filter the values to be defaulted to only resolution, other people say it is a parameter for high priority..... blah....

So after reconfiguring the xserver-xorg packages I rerun the nVidia installer, uninstalled previous drivers and installed them again... after that>  sudo /etc/init.d/gdm restartand that was it. Everything back to normal.

---

