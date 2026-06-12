---
title: "NVIDIA video stopped working after update"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by mrf on 2006-07-10
Hi,

I've had my nvidia video driver stop functioning out of the blue after an update manager update.

The log I'm getting from X is :
```
xauth:  creating new authority file /home/alistair/.serverauth.7071

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-ubuntu1 x86_64
Current Operating System: Linux vger 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 x86_64
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  8 17:05:43 2006
(==) Using config file: "/etc/X11/xorg.conf"

(EE) /usr/lib/xorg/modules/drivers/nvidia_drv.so is an unrecognized module type
(EE) Failed to load module "nvidia" (unknown module type, 6)
(EE) No drivers available.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"

      after 0 requests (0 known processed) with 0 events remaining.
```
I had installed the driver from the nvidia installation script. I removed that and installed from synaptic. But I get the same result in both cases.

Googling shows other people have the same issue and posting on the nvnews forum about it, but without any solution as of yet. any ideas?

---

### Post by tseliot on 2006-07-10
Please read this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

and if you want you can try my script:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by mrf on 2006-07-10
Hi Tseliot,

I had used your script originally to install the driver, and it had worked fine for months. I've been thru reinstalling the driver half a dozen times due to new kernels. I've done exactly the same thing this time. But it doesn't work. The nvidia driver has been installed fine, by your script, and via synaptic. It just won't load the module for some reason. 

Here's someone else with the same issue : [http://www.nvnews.net/vbulletin/showthread.php?t=72466](http://www.nvnews.net/vbulletin/showthread.php?t=72466)

edit: I'm not sure exactly what module it was that it installed, that caused it to stop working, but I'm fairly sure it wasn't a new kernel, as I haven't had a new kernel for a few weeks. I think it might have been xserver-xorg package, but I wasn't paying much attention at the time.

---

### Post by tseliot on 2006-07-10
> **mrf said:**
> Hi Tseliot,

I had used your script originally to install the driver, and it had worked fine for months. I've been thru reinstalling the driver half a dozen times due to new kernels. I've done exactly the same thing this time. But it doesn't work. The nvidia driver has been installed fine, by your script, and via synaptic. It just won't load the module for some reason. 

Here's someone else with the same issue : [http://www.nvnews.net/vbulletin/showthread.php?t=72466](http://www.nvnews.net/vbulletin/showthread.php?t=72466)

edit: I'm not sure exactly what module it was that it installed, that caused it to stop working, but I'm fairly sure it wasn't a new kernel, as I haven't had a new kernel for a few weeks. I think it might have been xserver-xorg package, but I wasn't paying much attention at the time.
Can you try point 13 of the Problems section of my guide? (I know it's a different problem)

---

### Post by mrf on 2006-07-10
ok, I assume 13 is disabling splash. I edited the menu.lst, removing splash from the def options line. Ran sudo update-grub, and rebooted. It boots up in  txt mode, and then fails when starting gdm. Same thing as before :
```
(EE) /usr/lib/xorg/modules/drivers/nvidia_drv.so is an unrecognized module type
(EE) Failed to load module "nvidia" (unknown module type, 6)
(EE) No drivers available.
```

edit: dunno if this means anything, but :
```
lsmod | grep nvidia
nvidia               5432600  0
i2c_core               26048  8 i2c_acpi_ec,tda9887,tuner,cx88xx,i2c_algo_bit,tveeprom,nvidia,i2c_nforce2
```

---

### Post by mrf on 2006-07-10
Ok, I've solved this, but I don't understand why...

```
sudo mv /usr/lib/xorg/modules/drivers/nvidia_drv.so /usr/lib/xorg/modules/drivers/nvidia_drv.so_old
sudo mv /usr/lib/xorg/modules/drivers/nvidia_drv.o /usr/lib/xorg/modules/drivers/nvidia_drv.so
```

for some reason the file has been installed incorrectly. ???

---

### Post by tseliot on 2006-07-10
> **mrf said:**
> Ok, I've solved this, but I don't understand why...

```
sudo mv /usr/lib/xorg/modules/drivers/nvidia_drv.so /usr/lib/xorg/modules/drivers/nvidia_drv.so_old
sudo mv /usr/lib/xorg/modules/drivers/nvidia_drv.o /usr/lib/xorg/modules/drivers/nvidia_drv.so
```

for some reason the file has been installed incorrectly. ???

Did you use the latest version of my script (0.41)?

---

### Post by mrf on 2006-07-10
no, hadn't realized it had been updated.

Thanks for your help man, you're a legend.

---

