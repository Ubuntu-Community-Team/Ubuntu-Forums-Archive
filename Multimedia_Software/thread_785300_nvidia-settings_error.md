---
title: "nvidia-settings error"
date: 2008-05-07
forum: Multimedia Software
---

### Post by chamstar on 2008-05-07
I have enabled the restricted driver but when I start nvidia-settings I get the following error:

ERROR: NV-CONTROL extension not found on this Display.
ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.
ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.
ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

Something is clearly wrong I had to play with the conf file to even get x to start. 

I'm on Ubuntu 7.04 (Feisty) and have had this exact video card working before - I recently did a clean install (and wish I hadn't).

"lspci | grep -i nvidia" reports:
04:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

xorg.conf [snippet]:
Section "Device"
	Identifier	"Device0"
	Driver		"nv"
	Vendorname	"NVIDIA Corporation"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

I used nvidia-xconfig to generate this and had to change the Driver to 'nv' to prevent an 'API version mismatch'.

Many thanks in advance, Cham.

---

### Post by Xiong Chiamiov on 2008-05-07
I've gotten my nvidia card to work until I reboot, but others have followed the same process I have and gotten (full) success.

Press Ctrl-Alt-F2 to get to a prompt - this will close down your GUI, so write these down first.
```

sudo apt-get remove nvidia-glx nvidia-glx-new
sudo /etc/init.d/gdm stop
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
sudo ./NVIDIA-Linux-x86-169.12-pkg1.run
startx

```
This will install the drivers from NVIDIA directly, rather from the repos.
BTW, since nobody wants to type out the whole filename, the next-to-last line, you can just type 
```

sudo ./N

```
then press tab, and it will complete it for you.

---

### Post by chamstar on 2008-05-07
Getting the drivers direct from NVIDIA was the way to go!
Now I am back to dual screen and have my xorg.conf backed up :)

Cheers.

---

### Post by Domie on 2008-07-13
> **Xiong Chiamiov said:**
> I've gotten my nvidia card to work until I reboot, but others have followed the same process I have and gotten (full) success.

Press Ctrl-Alt-F2 to get to a prompt - this will close down your GUI, so write these down first.
```

sudo apt-get remove nvidia-glx nvidia-glx-new
sudo /etc/init.d/gdm stop
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
sudo ./NVIDIA-Linux-x86-169.12-pkg1.run
startx

```
This will install the drivers from NVIDIA directly, rather from the repos.
BTW, since nobody wants to type out the whole filename, the next-to-last line, you can just type 
```

sudo ./N

```
then press tab, and it will complete it for you.

Same here: success until I reboot.

Solution?

---

### Post by Domie on 2008-07-13
AAah, solution:

sudo gedit /etc/default/linux-restricted-modules-common
modify the last line 
```

DISABLED_MODULES="nv"
```

---

