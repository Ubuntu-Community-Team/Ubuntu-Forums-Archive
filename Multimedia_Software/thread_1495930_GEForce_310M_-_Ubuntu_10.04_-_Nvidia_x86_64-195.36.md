---
title: "GEForce 310M - Ubuntu 10.04 - Nvidia x86_64-195.36.24"
date: 2010-05-28
forum: Multimedia Software
---

### Post by belfasttim on 2010-05-28
Hi all-- I just got a new laptop, a Sony Viao VPCF1. It's got an Nvidia GEForce 310m.

I activated the recommended hardware driver in the ubuntu system/administrator/hardware drivers dialog, rebooted, and the screen is split down the middle, and low res is the only mode it will run in. 

Running the Nvidia settings utility gives the error "you do not appear to be using the Nvidia X driver-- run nvidia-xconfig". When I do this and restart X, no change.

It appears it's unable to detect the screen/device combo in the x config file.

I uninstalled the recommended driver and downloaded the newest driver from Nvidia and did a manual install of that, and the same problem.  

Any pointers appreciated!

---

### Post by matstumpf on 2010-06-29
so, any ideas?
i`m having the same problem with VAIO VPCF111FX= i7/NV 310m

i tried installing Synaptic drivers, than the resolution is OK, but when i open NVIDIA X server, gives me the same message, and i can't activate any visual effects..

tanks!

---

### Post by Loksta on 2010-09-14
Same problem here. Did you ever figure it out? My touchpad doesn't work either.

---

### Post by Linuxforall on 2010-09-15
Install it via x-swat ppa which also comes with newer touchpad drivers, my latest Toshiba C650 works fine on Ubuntu.

---

### Post by Loksta on 2010-09-16
Thanks

---

### Post by tejota on 2010-09-18
I have the same problem with a Dell Vostro 3300 and Ubuntu Studio 10.04 64bits. After trying a bunch of things in several tutorials, ended up with the driver activated but not in use. 

Tried editing the /etc/X11/xorg.conf   and changing the Driver from "nouveau" to "nvidia" but no luck.

Anyone? : (

---

### Post by tejota on 2010-09-18
I solved my problem! See this:
[http://ubuntuforums.org/showpost.php?p=9861792&postcount=23](http://ubuntuforums.org/showpost.php?p=9861792&postcount=23)

---

### Post by changomuc on 2010-10-15
This didn't work for me ... when I start after installing, I get the shell, and when I try "startx" it seems it can't find the screen device ....

---

