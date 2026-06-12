---
title: "Nvidia 177,180 Drivers Step X Step"
date: 2009-03-05
forum: Multimedia Software
---

### Post by Ripose on 2009-03-05
Follow these directions, substituting the correct package for your Video card E.G. 173, 177, 180 etc

Chapter 2. Minimum Software Requirements

CHECK WITH TERMINAL METHOD
sudo not required

Software Element-----Min Requirement-----Check With...
Note: You will have Xterm, but I put the XFree in the list anyways.
Linux kernel-----------------2.4.7---------------cat /proc/version
XTerm------------------------ 229----------------xterm -version
XFree86/X.Org-----------4.0.1/6.7-----------XFree86 -version/Xorg -version
GDM--------------------------2.20.7-------------gdm --version
Kernel modutils-----------2.1.121------------insmod --version


If you need to build the NVIDIA kernel module: (probably will)

Software Element----Min Requirement-----Check With...
binutils------------------------2.9.5----------------size --version
GNU make------------------ 3.77----------------make --version
gcc--------------------------2.91.66---------------gcc --version


CHECK WITH SYNAPTIC PACKAGE MANGER METHOD
root password required
Just scroll through the list to see what you have installed.

Now download the Nvidia 180 driver from here:
[http://www.nvidia.com/object/linux_disp ... 80.29.html]("http://www.nvidia.com/object/linux_display_ia32_180.29.html") (32 bit)
[http://www.nvidia.com/object/linux_disp ... 80.29.html]("http://www.nvidia.com/object/linux_display_amd64_180.29.html") (AMD 64 bit)

Nvidia 177 driver here:
[http://www.nvidia.com/object/linux_display_ia32_177.82.html (32 bit)]("http://www.nvidia.com/object/linux_display_ia32_177.82.html")
[http://www.nvidia.com/object/linux_display_amd64_177.82.html (64 bit)]("http://www.nvidia.com/object/linux_display_amd64_177.82.html")

Save the file to an easy to remember directory E.G. /home

Hit [CTRL]+[ALT]+[F2]
Enter username & password if prompted
sudo /etc/init.d/gdm stop
password
cd /home
dir
sudo sh NVIDIA-......... (full file name)
answer yes to all questions

NOTE: Even after successfully installing the Nvidia driver I can still not use Compiz Effects or play 3D Chess.

---

### Post by damis648 on 2009-03-05
Double Post.

---

### Post by damis648 on 2009-03-05
I would recommend [this]("https://launchpad.net/~anders-kaseorg/+archive/ppa") PPA for the 180 driver... just head to the restricted drivers manager and installer any previous driver, then open Synaptic and install the modaliases and the driver package for 180, go back to the drivers manager and install 180. Reboot. Cheers!:popcorn:

---

### Post by Ripose on 2009-03-05
What makes you think this is a double post?

Your solution does not really help beginners.

---

### Post by damis648 on 2009-03-05
> **Ripose said:**
> What makes you think this is a double post?
It's not a double post, mine was.
> **Ripose said:**
> Your solution does not really help beginners.
This one doesn't really either, does it?

---

### Post by jessecollins on 2009-03-05
> **damis648 said:**
> I would recommend [this]("https://launchpad.net/~anders-kaseorg/+archive/ppa") PPA for the 180 driver... just head to the restricted drivers manager and installer any previous driver, then open Synaptic and install the modaliases and the driver package for 180, go back to the drivers manager and install 180. Reboot. Cheers!:popcorn:

Thanks for posting this.  Didn't even know that these drivers were available in the repositories.

In case anyone else wants to update their nVidia driver to 180, I took the following steps...

1) As damis648 mentioned, go to Synaptic and install nvidia-180-kernel-source & nvidia-180-modaliases.  Note: This will uninstall 177.
Or you can just run the following in the console:
```
sudo apt-get install nvidia-180-kernel-source
sudo apt-get install nvidia-180-modaliases
```
2) Reboot.  (At least I had to before I saw 180 in the list of restricted drivers.)
3) Check out the restricted drivers (System -> Administration -> Hardware Drivers) and you should now see 180.  ;)

Jesse

---

