---
title: "Unable to login to gui after uninstall of EnvyNG"
date: 2009-11-22
forum: Multimedia Software
---

### Post by sticke4 on 2009-11-22
Hi, I am quite new to Ubuntu and have run into a problem where I am unable to login to my computer at all. I am running Karmic on the computer that I am having problems with.

     I installed EnvyNG, so that I could install newer ATI drivers for my video card to run 3d applications better. I ran EnvyNG updated my driver successfully, and rebooted. During the reboot, after the Grub loader screen, I got to the screen 'libgcrypt version: 1.4.4'. Although at this screen all the text on the screen was flashing. It then, instead of normally going to my GUI login like normal, it used a text interface for asking my login and password. Although, most likely because of the constant flashing, it was only recognizing a few of the keys I was pressing for my username.  I believed it was a problem with the video driver update. 

     As said by on the Envyng FAQ if something wasn't working, I booted into recovery mode and uninstalled the program (which I presume also uninstalls the driver update and reverts to the ubuntu default driver). Yet after rebooting the text on the 'libgcrypt version: 1.4.4' screen still flashes and I can't get to the GUI login.

     I desperately need a solution to this problem, because I am unable to use my computer. Sorry for the long post.

---

### Post by sticke4 on 2009-11-22
It seems that there was a problem with my xorg.conf file. I had to change all instances of fglrx in the xorg.conf file with at. 
Phew! I am so happy that the crisis was averted, and I didn't have to reinstall ubuntu.

---

