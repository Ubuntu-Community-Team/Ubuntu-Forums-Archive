---
title: "nvidia = gdm crash?"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by Martinv on 2006-06-11
Hello all. Today I've formatted, and installed a fresh ubuntu 6.06 install from cd. I though encounter some problems, when using the nvidia-driver....
When the install was fresh, I tried to run glxgears - and it worked, running by 1 FPS or so. Not good. 

I installed automatix, and then installed the nVidia-driver from there. When this is happening, it changes in the xorg.conf, 'nv' to 'nvidia'. But when I then reboot, it can't start gdm! It just freezes. Then I have to change 'nvidia' back to 'nv' again.

I've tried to re-install the driver via apt-get, but that solves nothing.
Right now, when I type 'glxgears', it says:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

When I do sudo nvidia-glx-config enable, it says:


Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.



(How) can I make it work?
It's a nVidia Geforce 4 GO 420 32mb, on i386


Sincerely,
Martin V

---

### Post by CronoDekar on 2006-06-11
While Automatix is good for the normal user, I don't think it handles it well when you need specialized stuff.  tseliot has a good way to install the Nvidia driver here:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Note that there's a special step for the GeForce GOs.

---

### Post by Martinv on 2006-06-11
Thanks for the reply,

I downloaded the latest driver, and followed 'method 2', of the mentioned guide. When done, I got an error, telling me I need driver 7174 instead of the newest.
Well, then. Downloaded 7174 driver, and followed method 1. Now, I get a fatal error, 'no screens found', when booting.

---

### Post by arnieboy on 2006-06-11
Please paste the results of the following command here:
```
lspci | egrep "GeForce"
```
We would like to add your card to the Automatix nvidia exceptions list.
Thanks,
Arnie

---

