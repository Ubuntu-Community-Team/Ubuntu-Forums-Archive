---
title: "nVidia Driver for GeForce 8400GS Ubuntu 9.04"
date: 2009-06-23
forum: Multimedia Software
---

### Post by Augustino on 2009-06-23
Hi

I am installing the nVidia driver propietary but never load the GUI
My motherboard is the DP45SG the which have two videocards ASUS GeForce 8400GS

I tried installing the version 173, 180 and 185, the process is completed correctly, but not show the Graphic Interface

In the /etc/var/log/Xorg.0.log say 

Fatal server error
No screens found

Also tried uninstalling the driver, the which do correctly, but still the problem is persistent dont start the Xserver when was uninstalled the driver
[B]
I need this driver because i need the four outputs of the two videocards, Can I get this without the nVidia driver?, Some idea?:confused::([/B]

---

### Post by Arup on 2009-06-23
Which driver are you trying to install, one in repos or the one from nvidia's site, in case its the later, make sure you have removed the one from repos and also removed linux restricted modules and linux restricted modules common from synaptic by ticking complete removal. Then do a sudo apt-get install build-esential and log out by doing a ctrl+alt+F1 login to tty do a sudo /etc/init.d/gdm stop and then do a sudo sh NVIDIAxxxxxxxxx make sure your nvidia driver is in home directory. Say yes to all the options and then do a sudo reboot, you will have your latest nvidia drivers on system.

---

### Post by overdrank on 2009-06-23
Hi and it sounds like you are using SLI with two graphics cards and this [thread]("http://ubuntuforums.org/showthread.php?t=884161") may help.

---

### Post by Augustino on 2009-06-24
> **Arup said:**
> Which driver are you trying to install, one in repos or the one from nvidia's site, in case its the later, make sure you have removed the one from repos and also removed linux restricted modules and linux restricted modules common from synaptic by ticking complete removal. Then do a sudo apt-get install build-esential and log out by doing a ctrl+alt+F1 login to tty do a sudo /etc/init.d/gdm stop and then do a sudo sh NVIDIAxxxxxxxxx make sure your nvidia driver is in home directory. Say yes to all the options and then do a sudo reboot, you will have your latest nvidia drivers on system.

I tried from nVidia drivers site the versions 96, 173,180 and 185, and I did it the what you said, but not load the interface graphic, only console, also tried uninstalling the driver with

To install
sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run --install -a

To uninstall
sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run --uninstall -a

When install removed linux restricted modules and linux restricted modules common from synaptic and stop gdm after I install the driver, but still the problem is continuing

How can I do it this? Have the four monitor without nVidia drivers? or if is needed, how can i install the drivers, because, never load the graphic interface, always appears the console login

---

### Post by slamhound on 2009-06-24
You might try running nvidia-xconfig -a (the -a tells it to enable all gpus).  

I have links to a more detailed description in a reply to another poster:
[http://ubuntuforums.org/showpost.php?p=7456380&postcount=17](http://ubuntuforums.org/showpost.php?p=7456380&postcount=17)

---

### Post by Augustino on 2009-06-24
> **slamhound said:**
> You might try running nvidia-xconfig -a (the -a tells it to enable all gpus).  

I have links to a more detailed description in a reply to another poster:
[http://ubuntuforums.org/showpost.php?p=7456380&postcount=17](http://ubuntuforums.org/showpost.php?p=7456380&postcount=17)

Say me the following error

Using X configuration file: "/etc/X11/xorg.conf".
FATAL: Module nvidia not found.
NVIDIA: failed to load the NVIDIA kernel module.

ERROR: Unable to determine number of GPUs in system; cannot honor
       '--enable-all-gpus' option.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


tried installing [http://download.nvidia.com/XFree86/nvidia-xconfig/nvidia-xconfig-1.0.tar.gz](http://download.nvidia.com/XFree86/nvidia-xconfig/nvidia-xconfig-1.0.tar.gz)

firstly I uncompressed and did 

make
make install

but when rebooted the xserver dont want start the x server, had what change between servers with control + alt + f7 or f9

**but appear be was not the driver installed properly **

---

