---
title: "Not using Nvidia X driver"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by phaed on 2007-12-19
I have a Nvidia GeForce FX 5500 graphics card.  I'm using the  2.6.22-14-generic kernel so I installed the proprietary Nvidia drivers for it.  Under System -> Administration -> Restricted Drivers Manager, it says that the Nvidia accelerated graphics driver is installed and in use.

However, when I log in from GDM, the screen goes blank temporarily (a few seconds), then GNOME loads.  When I go to Applications -> System Tools -> Nvidia Settings, it says

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Gnome works perfectly fine, but I'm unnecessarily using up ~70 mb of memory (with Xgl) that could be handled by the graphics card.  I've tried running nvidia-xconfig, but it doesn't help.

Attached is my xorg.conf file.

---

### Post by lauck99 on 2007-12-19
This may be attempting to solve a simple problem with a sledge hammer but you can try running these commands and then reinstall the driver:

sudo apt-get remove --purge nvidia-glx 

sudo apt-get remove --purge nvidia-glx-new

sudo rm -fvr /etc/init.d/nvidia*

---

### Post by starcannon on 2007-12-19
CTRL-ALT-F1```
cp /etc/X11/xorg.conf /home/you
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
sudo /etc/init.d/gdm restart
```
That should do it for you, be sure to open a terminal and ```
sudo nvidia-settings
``` and make any changes you like and then save and exit and then CTRL-Backspace to restart the X server once more.

Cheers,
Starcannon

---

### Post by phaed on 2007-12-20
That didn't work.

---

### Post by hanniph on 2007-12-20
i'm having exactly the same problem. 

That extra memory loss (used by Xgl)  is too much for my system, so while i haven't found any solution, i find it better 
not to use nvidia driver at all. :(

---

### Post by phaed on 2007-12-20
Yep, right now I'm just keeping the Nvidia driver uninstalled and operating without desktop effects.

Kind of sucks though, because it works....but not quite.

---

### Post by punklinux on 2007-12-22
hey I'm having the same problem, also my friend might know how to fix it when u fixes mine I'll have him post what he did. but just like you when i use the restricted driver and then enable the desktop effects my computer acts like a piece of crap. so I'm currently using the on broad video instead of my nvidia card.

---

### Post by hanniph on 2008-01-15
I managed to solve it

I followed [this how-to]("http://ubuntuforums.org/showthread.php?t=569654&highlight=LIBGL_DEBUG%3Dverbose+glxinfo%7Cless&page=2") until the 8th step.

---

### Post by phaed on 2008-02-08
I found a solution!

I used [Envy]("http://albertomilone.com/nvidia_scripts1.html").

---

