---
title: "ATI Driver"
date: 2008-04-25
forum: Multimedia Software
---

### Post by oasmar1 on 2008-04-25
I installed hardy heron and it asked me to do enable the driver for ATi. I ticked the box for 3d support and it told me to restart which i did.
Then when ubuntu started up it just went to a black screen. How do I enable the Ati Graphics Cards?

My card is an X1650 pro agp

---

### Post by Rocket2DMn on 2008-04-25
Try this:
CTRL+ALT+F1 to get to a tty, login at the tty and run
```
sudo apt-get remove --purge xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg -phigh
startx
```
Hopefully you should be back in the GUI now.  You should now try to install the restricted drivers from ATI's website using a program called EnvyNG which is available in the repositories.
```
sudo apt-get install envyng-gtk
```
If you the program doesn't start right away, go to Applications->System Tools->EnvyNG and select to install the ATI restricted drivers using automatic detection.

---

### Post by oasmar1 on 2008-04-26
CTRL-ALT-F1 does nothing. I have since removed ubuntu and installed again, however, the graphics are really slow... :(

---

### Post by Rocket2DMn on 2008-04-28
Sorry for the delayed response.  Reboot your computer and at GRUB, select the second option to enter the recovery mode kernel.  This will drop you at a root shell, run
```
sudo apt-get remove --purge xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg -phigh
reboot
```
Let it reboot normally, and hopefully you should be able to access the GUI.  Login, open a terminal and run
```
sudo apt-get install envyng-gtk
```
If EnvyNG doesn't start automatically, just go to Applications->System Tools->EnvyNG and select to install the ATI restricted drivers using automatic detection.

---

