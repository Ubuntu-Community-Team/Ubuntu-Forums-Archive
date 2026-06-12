---
title: "[SOLVED] EnvyNG packages not installed"
date: 2008-07-10
forum: Multimedia Software
---

### Post by kolibri on 2008-07-10
I upgraded to Hardy and broke the NVIDIA driver.

I installed EnvyNG and tried to install the NVIDIA drivers for Hardy, but received the following error:

The following packages are not installed
nvidia-new-kernel-source-envy
nvidia-glx-new-envy
nvidia-glx-new-dev-envy

followed by:
Couldn't find package
nvidia-new-kernel-source-envy

I'm not sure where to go from here, I previously had tried these guides to get the NVIDIA drivers working:
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)
[http://ubuntuforums.org/showthread.php?t=596875](http://ubuntuforums.org/showthread.php?t=596875)
and then removed all nvidia components before installing EnvyNG.

any help to get my the video drivers working so I can go back to work would be appreciated.

---

### Post by zbc8103 on 2008-07-11
I guess  you sources.list is not good .
so you Couldn't find package
nvidia-new-kernel-source-envy
 

add this you sources.list 


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse


but you OS must is 8.04 hardy .
now  you install nvidia-new-kernel-source-envy
apt-get install nvidia-new-kernel-source-envy

good luck  !

---

### Post by petzworld999 on 2008-07-11
Try entering this into a terminal:
```

sudo apt-get install nvidia-glx-new

```

If that does not work, try posting your /etc/X11/xorg.conf file and I'll look at that for possible issues. 

```

gedit /etc/X11/xorg.conf

```

---

### Post by kolibri on 2008-07-11
thanks zbc8103, I added all of those specific sources, and then EnvyNG found those packages and got the Nvidia dialog up and running.  I had already enabled universe and multiverse on the Ubuntu software tab of Software sources, so why wasn't that sufficient?

I still found nvidia-settings to be fairly clunky, but I have a decent resolution now, and both monitors working.

petzworld999- I had already tried  sudo apt-get install nvidia-glx-new, but had removed all nvidia files before trying EnvyNG.  I've got it working now, thanks.

---

