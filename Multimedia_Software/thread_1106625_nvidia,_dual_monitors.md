---
title: "nvidia, dual monitors"
date: 2009-03-25
forum: Multimedia Software
---

### Post by jbfriend on 2009-03-25
please tell me how to fix this:


You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

i don't understand what nor how to do this.

---

### Post by thehipho on 2009-03-25
Did you already try to install and activate the Nvidia driver: system> administrator> hardware drivers.

After that you can edit Xorg.conf, the line in "Section Device" change the "nv" to show: Driver  "nvidia".

Hope that helps.

---

### Post by norwoods on 2009-03-26
> **jbfriend said:**
> please tell me how to fix this:


You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

i don't understand what nor how to do this.

you get a command line by starting Applications-->Accessories-->Terminal
you get admin(root) privileges by starting a program with sudo or gksu for gnome programs. type this into the terminal:
sudo nvidia-xconfig

---

### Post by jbfriend on 2009-03-26
> **norwoods said:**
> you get a command line by starting Applications-->Accessories-->Terminal
you get admin(root) privileges by starting a program with sudo or gksu for gnome programs. type this into the terminal:
sudo nvidia-xconfig
thank you both for the above. now i have Nvidia in the "device" driver. when i try to save i get the reply:

Unable to remove old X config backup file. i must need to do that myself?

---

### Post by SuperSonic4 on 2009-03-26
Are you running it as root or as user? Only root can edit/remove xorg.conf

---

### Post by norwoods on 2009-03-26
to run nvidia settings to create the dual monitor configuration, you get a command line by starting Applications-->Accessories-->Terminal
you get admin privileges by starting a program with gksu for gnome programs:
gksu nvidia-settings
when the nvidia gui interface is running, click X Server Display Configuration. 
click Configure...
click the TwinView radio button
click OK
set up anything you want
click Save to X Configuration File
click Quit

---

