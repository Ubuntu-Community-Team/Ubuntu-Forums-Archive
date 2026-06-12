---
title: "error message from nvidia GUI: &quot;run nvidia-xconfig as root&quot;"
date: 2009-11-11
forum: Multimedia Software
---

### Post by nss0000 on 2009-11-11
Gents:

Jaunty hosed my entire nv-driver setup removing a working 190.xx setup. Now I have NO installed NV driver and running the nv-gui get a message:

run nvidia-xconfig as root

What does it mean and how do I do this: I have tried dloading the listed nv190.47 drivers using package-manager. but nothing happens.

---

### Post by konqueror7 on 2009-11-11
```
sudo nvidia-xconfig
```

---

### Post by nss0000 on 2009-11-11
> **konqueror7 said:**
> ```
sudo nvidia-xconfig
```

Sure I've done that ... and always get:

*****
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
*****

I have no idea what "that" means  ... or what action(s) it implies/requests/requires.

---

### Post by konqueror7 on 2009-11-11
this command will setup your xorg.conf to be 'nvidia compatible' so to say...after you've done that, the effects would only be applied after X has been restarted...

for an overview, here how i install my nvidia driver...
```

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-*
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start

```

this is assuming you are working in the current directory of the nvidia driver...hope it helped...

---

### Post by nss0000 on 2009-11-11
> **konqueror7 said:**
> this command will setup your xorg.conf to be 'nvidia compatible' so to say...after you've done that, the effects would only be applied after X has been restarted...

for an overview, here how i install my nvidia driver...
```

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-*
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start

```
this is assuming you are working in the current directory of the nvidia driver...hope it helped...

On the bad-side.... all your commands fail to execute or return "null"!!!

On the good side... after miserably failing, "Jaunty system(?)" has automagically and unobserved installed the proper 190.xx driver and nvidia gui. 

On the weird side.... I did --- NOTHING OF VALUE -- to recover from the disaster of losing driver+xserver+??. I might as well have sprinkled hot chicken_blood over the tower.

---

### Post by konqueror7 on 2009-11-12
> **nss0000 said:**
> On the bad-side.... all your commands fail to execute or return "null"!!!

On the good side... after miserably failing, "Jaunty system(?)" has automagically and unobserved installed the proper 190.xx driver and nvidia gui. 

On the weird side.... I did --- NOTHING OF VALUE -- to recover from the disaster of losing driver+xserver+??. I might as well have sprinkled hot chicken_blood over the tower.

my command are meant to be a preparation and also the installation in which i would assume that the nvidia driver from the nvidia site is already there. so returning null or nothing in some commands can happen. but this is the way i install my drivers. i suggest you just install the latest driver in the repos, and do the nvidia-xconfig and restart...

---

