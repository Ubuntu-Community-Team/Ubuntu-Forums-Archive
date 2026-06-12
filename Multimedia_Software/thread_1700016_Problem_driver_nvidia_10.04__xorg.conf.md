---
title: "Problem driver nvidia 10.04  xorg.conf"
date: 2011-03-04
forum: Multimedia Software
---

### Post by ephramdoyle on 2011-03-04
*Before, everything worked properly. But the latest update has caused an error... *:frown:

Laptop Model: N51V 
Features: Intel Core 2 Duo - NVIDIA GeForce 240M GT 
Ubuntu Version: 10.04 LTS - Lucid Lynx version - 

[B]Problem: 
Successfully install the graphics drivers. 
If I install the drivers, in the beginning goes into a loop before reaching the login (alternating between code and logo of nvidia). [/B]

As a patch to load the OS. I deleted the contents of the folder / etc/X11 and I have copied the data from a live cd. 
This allows me to access directly. But I haven't the maximum resolution and I have no 3D 3D acceleration. 
In addition, once I log while loading the desktop can see the following message: 

[http://img232.imageshack.us/i/malaconf.jpg/]("http://img232.imageshack.us/i/malaconf.jpg/")

I tested methods: 

[B]1. I uninstall everything related to nvidia 
[/B]- In synaptic uninstall everything nvidia starts. 
- In console: 
sudo apt-get - purge remove xserver-xorg-video-nouveau 
sudo apt-get - purge remove nvidia * 
sudo nvidia-uninstall 
sudo sh NVIDIA-Linux-x86-260.19.36.run - uninstall 

- In the / etc/X11 / delete the xorg.conf 

[B]2. Disclaimer official website driver "NVIDIA GeForce GT 240M for linux32" 
[/B]- NVIDIA-Linux-x86-260.19.36.run 

[B]3. I tried installing the drivers in 2 ways: 
[/B]_A. - Closing session. In the login screen press Ctrl + Alt + F1. _
- In console: 
sudo service gdm stop 
su - (enter as root) 
sudo sh NVIDIA-Linux-x86-260.19.36.run 
- Install without error 

[U]B. - I create a file "instalar_NVIDIA" in writing: 
[/U]# / Bin / sh 
nvidia-uninstall 
gdm stop 
bash NVIDIA-Linux-x86-260.19.36.run 
gdm start 

Restart the OS. I choose the second option (recovery) rootnet 
And I write: sh instalar_NVIDIA 
- Install without error 

When installation has completed, says:
> "Would you like to run the nvidia-xconfig utility to update your X configuration Automatically 
That file so the NVIDIA X driver will be Used When you restart X? 
Any pre-existing X configuration file will have backed up. 
[YES] [NO] 

Select "YES" to be set automatically: 
> "Your X configuration file has Been Successfully updated. 
Accelented Installation of the NVIDIA Graphics Driver for Linux-x86 (version: 260.19.30) is complete. " 
     
If "NO": 
> "Installation of the NVIDIA Graphics Driver for Linux Accelented-x86 (version: 260.19.30) is complete. 
Please update your XF86Config or xorg.conf file as Appropriate; 
see the file usr/share/doc/NVIDIA_GLX-1.0/README.txt for details. " 
     
The xorg.conf file generated: 
[http://paste.ideaslabs.com/show/605HylWyjb]("http://paste.ideaslabs.com/show/605HylWyjb")
     
   **_ * In any case to restart when it shows the nvidia logo go back .. _**
     Sign in loop showing these 2 screenshots: 
[http://img46.imageshack.us/g/24314766.jpg/]("http://img46.imageshack.us/g/24314766.jpg/")
     loop: [http://img717.imageshack.us/i/bucle1.jpg/]("http://img717.imageshack.us/i/bucle1.jpg/") and [http://img638.imageshack.us/i/bucle2.jpg/]("http://img638.imageshack.us/i/bucle2.jpg/")
     
**What I can do to install it correctly?**

---

### Post by BicyclerBoy on 2011-03-04
Are there any clues in output of:

dmesg

or in log file
/var/log/Xorg.0.log

You have the correct kernel headers packages ?

---

### Post by ephramdoyle on 2011-03-04
Hi! Thanks for answering.


**_dmesg_**
[http://paste.ideaslabs.com/show/2zukMW6ecR](http://paste.ideaslabs.com/show/2zukMW6ecR)

**_LOG FILE /var/log/Xorg.0.log_**
[http://paste.ideaslabs.com/show/T8onuuryWr](http://paste.ideaslabs.com/show/T8onuuryWr)

My current file **xorg.conf**:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I just do this:

```
**ephram@STRIKE:~$ sudo apt-get update**
**ephram@STRIKE:~$ apt-cache search linux-headers-$(uname -r)**
linux-headers-2.6.32-29-generic - Linux kernel headers for version 2.6.32 on x86/x86_64
linux-headers-2.6.32-29-generic-pae - Linux kernel headers for version 2.6.32 on x86
[B]ephram@STRIKE:~$ sudo apt-get install linux-headers-$(uname -r)
[/B]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
linux-headers-2.6.32-29-generic ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```
Full results of the command "sudo apt-get update": [http://paste.ideaslabs.com/show/vf3nZe3IXI](http://paste.ideaslabs.com/show/vf3nZe3IXI)

I understand that the headers are correct. Is this correct?

---

### Post by Bo0ddha on 2011-03-05
Having same problem after recent update.  Tried the same ctrl alt f1 method and same results.

---

### Post by ephramdoyle on 2011-03-05
any solution?

---

### Post by BicyclerBoy on 2011-03-07
Sorry. I don't see any errors in the dmesg or Xorg.0.log files..

The xorg.conf file posted can not be actually used because you are not loading the vesa driver.

The xorg.conf generated by the nvidia installer looks better..

If this problem was caused by an update you may have to force an older version of something..

I always try to update video drivers on a different reboot cycle to kernel updates..
I'm running same kernel version (64 bit) graphics driver & GPU CPU okay.

Try an external mouse/keyboard & disable the touchpad ?

---

