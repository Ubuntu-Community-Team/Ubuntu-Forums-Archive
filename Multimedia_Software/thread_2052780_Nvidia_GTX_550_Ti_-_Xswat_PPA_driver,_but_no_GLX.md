---
title: "Nvidia GTX 550 Ti - Xswat PPA driver, but no GLX"
date: 2012-09-03
forum: Multimedia Software
---

### Post by houstonbofh on 2012-09-03
I am running Ubuntu 10.04 with full updates, and [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) and I have a Gforce GTX 550 Ti.  (Needed the PPA for this card to work at all on 10.04)  Graphics work, but nvidia-settings shows "Failed to query the GLX server vendor."  GL games fail...  I remember this working at one time, but have not done any gaming in quite a while.  Anyone have any hints?

Before you start...

1) No 12.04 for me.  Unity interferes with the way I work too much and this is primarily a work machine.  The other options (KDE, Cinnamon, Mate, Xubuntu...) may eventually work, but I do not have time to learn a new system right now.

2) A reinstall is possible, but it will take a lot of work to get everything back the way it is set up.

3) I really want to fix this, not mask it.  I can not see how this could be happening, and that really bugs me!  I mustn't let the computer win! :)

---

### Post by cuyo01 on 2012-09-04
1)you can check *unity revamped* and see if it proves usefull to you, it works for 12.04. [http://www.webupd8.org/2012/05/how-to-get-dodge-windows-and-minimize.html](http://www.webupd8.org/2012/05/how-to-get-dodge-windows-and-minimize.html)

2) you can backup your /home/user/ directory to backup the configurations of your installed programs (hidden ./nameapp directories)

3)it happened to me once on my ubuntu 12.04 + gtx550 ti, it was because something got messed with an update of components of xorg and an update of the driver; the solution for me was to uninstall (purge) the nvidia drivers, download the latest driver from nvidia site and manually install from TTY the driver. the nvidia driver need to be uninstalled first, updating the driver dont solve the problem.

the easy way to install the nvidia driver could be:

take note of these instructions on paper since we need to stop x server.

download the latest driver from nvidia site acordly to your architecture and save it in your home directory.

open a TTY (ctrl+alt+f1) and enter your user name and pass

you will be in a terminal in your home directory, then type **sudo stop lightdm**, this will stop the x server

uninstall any previous nvidia driver using the driver you donwloaded with the commaand **sudo sh NVIDIA-Linux-xxx-xxx.xx.run --uninstall** where the xxx are the version/architectute number dof the driver (in my case is NVIDIA-Linux-x86-304.43.run), you can just type "sudo sh NVIDIA" with nvidia in CAPS and then hit tab to autocomplete the driver name, remember that filenames are case sensitive.

follow the instructions on screen, the program will remove the driver as best it can.

**DONT REBOOT/SHUTDOWN YOUR PC YET**

run **sudo sh NVIDIA-Linux-xxx-xxx.xx.run** to actually install the new driver, when promted to install dpkg modules choose yes, when prompted for let nvidia-xconfig create/modify a new x config file choose yes.

when you returned to terminal you can reebot (ctrl+alt-del)

---

