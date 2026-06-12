---
title: "Nvidia Drivers For Intrepid Ibex (8.10)"
date: 2009-03-14
forum: Multimedia Software
---

### Post by jgeboski on 2009-03-14
Hi all,

I am trying to get my nvidia drivers installed in Ubuntu 8.10.  I have tried installing nvidia-glx-177 and installing it from the restricted drivers part of Ubuntu.  They supposedly install fine but, when I reboot all i get is Xserver not start up right.  So i uninstall the nvidia drivers reboot and Xserver will start up fine.  Any help would be greatly appreciated.

Thanks,
James

---

### Post by norwoods on 2009-03-14
i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

open System--Administration--Hardware Drivers.
if there is an active video driver, click on it and then nclick Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

---

### Post by jgeboski on 2009-03-14
Thank you very much.  I will certainly try when i get off the FAP with Hughesnet.

---

### Post by jgeboski on 2009-03-14
Still no go.  I installed them in the order listed above.  For some reason i can not get envyng going in 8.10 either.  I had it working fine in 8.04.  I am running 2 x 8800 Ultra and it seems that people are not getting the driver installed with 2 cards in.

Thanks again,
James

---

### Post by inobe on 2009-03-14
first thing first' have you gotten all the updates ?

also include if this is an upgrade......

just to be sure' in terminal type

```
sudo apt-get update
```

and when that activity in terminal is done' close terminal and wait for the update notification in top right corner.

---

### Post by hobo on 2009-03-14
Follow the directions on this page: [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") It will do it all for you.

---

### Post by norwoods on 2009-03-14
> **jgeboski said:**
> Still no go.  I installed them in the order listed above.  For some reason i can not get envyng going in 8.10 either.  I had it working fine in 8.04.  I am running 2 x 8800 Ultra and it seems that people are not getting the driver installed with 2 cards in.

Thanks again,
James

there have been some threads that indicate you need to put the pci addresses of each gpu in Xorg.conf to get two gpu systems running but i have one gpu and have not paid much attention.

---

### Post by jgeboski on 2009-03-14
I tried installing EnvyNG for gnome(envyng-gtk) and tried to start it.  Also i uninstalled envyng-gtk and installed just the core (envyng-core) and i keep getting these exact same issues with both:

```
Traceback (most recent call last):
 File "interface.py", line 428, in <module>
   a = Interface()
 File "interface.py", line 126, in __init__
   self.abstract = abstraction.Abstraction(progress, True)
 File "/usr/lib/python2.5/site-packages/Envy/abstraction.py", line
39, in __init__
   self.driverDetails = self.hardware.selectDriver()
 File "/usr/lib/python2.5/site-packages/Envy/detection.py", line 248,
in selectDriver
   if 173 in candidates['nvidia'] and 177 in candidates['nvidia']:
TypeError: list indices must be integers
```

Thanks again,
James

---

### Post by jgeboski on 2009-03-16
I can confirm that only one graphics card will boot.  Two will not.

---

