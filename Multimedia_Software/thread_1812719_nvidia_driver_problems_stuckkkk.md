---
title: "nvidia driver problems stuckkkk"
date: 2011-07-26
forum: Multimedia Software
---

### Post by jay_jay_01 on 2011-07-26
helppppp someone please


hi i updated  my nvidia driver im running ultimate gamers edition 2.6 and now it only  boots as far as  terminal 1. i am a newbie and am completely lost. of  course i have searched google high and low and seems to be a common  problem however i have tried editing the xconf/xorg cnt remeber the name  iv tried using the restore mode which is second on the boot list and  have tried using the live cd to boot into graphics mode none seem to do  the trick if someone could help with an easy method i would really  appreciate it i.e through using the live cd or something as the commands  for the terminal are a pain for me also i would put up the xconf file  up but i only no how to view it through the cd i dnt no how to copy it  to usb to place on here

any help anything would be appreciated

---

### Post by lkjoel on 2011-07-26
Try running in the Terminal window:
```
sudo startx
```

---

### Post by jay_jay_01 on 2011-07-29
hi i have tried that and got the following error code i have attached photos of the full error code for you to have a look at

---

### Post by BicyclerBoy on 2011-07-29
Never heard of your ubuntu remix..
Exactly how did you try to update the nvidia driver ?
You could post the file (as attachment .txt )..
/var/log/Xorg.0.log

My guess is that your Xorg & driver & kernel do not match..

uname -r
xdpyinfo | head

& the nvidia X server/driver is broken so ..

---

### Post by jay_jay_01 on 2011-07-29
its ubuntu ultimate edition i pressed ctrl alt and f1 and had to stop the server then i pointed towhere the driver update  was on my desktop and it installed itself and im a newbie im not that advanced to copy the file to usb to add on here i dnt no how to

and what does this mean???????

:     uname -r
      xdpyinfo | head

---

### Post by BicyclerBoy on 2011-07-29
Okay.. the install method you used is the nvidia install script method & it works outside of the package management system.
(run from console login with X server stopped by sudo service gdm stop).

The installer failed because either your kernel headers package is/was missing or tools are missing.

You run from terminal/console login
uname -r

This reveals your kernel version..
You need to install the kernel headers package & build-essential tools..

You should have read the nvidia driver readme** first** & you should not have attempted this without a basic understanding..

You would have been well advised to get the driver package from:
x-swat ppa or xorg-edgers ppa.

---

