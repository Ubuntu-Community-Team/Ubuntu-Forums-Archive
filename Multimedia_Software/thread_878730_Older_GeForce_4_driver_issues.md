---
title: "Older GeForce 4 driver issues"
date: 2008-08-03
forum: Multimedia Software
---

### Post by drewcoon on 2008-08-03
Hi! After a virus scare and a stolen credit card number, I convinced my mom to install Ubuntu on a second hard drive in a dual boot setup. So far, it's working great... Except for the graphics card.

My mom's computer has an older GeForce 4 MX AGP graphics card, and I've tried everything from the driver installer off the site to Envy. When I setup the drivers, I:

ctrl + alt + f1 to terminal
sudo killall gdm
run driver installer
sudo gdm

at this point, the screen blinks three times and then I get a "no signal" message on the monitor. To fix it, I have to

sudo dpkg-reconfigure -phigh xserver-xorg 

to get a fresh xorg.conf, then I can get the GUI to work again, minus the 3D acceleration.

Could it be a problem with blacklisted modules? which ones should I have blacklisted in /etc/default/linux-restricted-modules-common? Which ones shouldn't be blacklisted?

I've been trying for hours and I'm really stumped... Can anyone help?

---

### Post by drewcoon on 2008-08-03
Bump, still in the process of trying everything I can think of, and no progress.

---

### Post by hansdown on 2008-08-03
Hi drewcoon. There are a number of nvidia drivers in the repos. Go to system> administration> synaptic package manager. If you type nvidia into the search bar, a number of drivers will show. Hope this helps.

---

### Post by drewcoon on 2008-08-03
> **hansdown said:**
> Hi drewcoon. There are a number of nvidia drivers in the repos. Go to system> administration> synaptic package manager. If you type nvidia into the search bar, a number of drivers will show. Hope this helps.

In the repos there are three drivers, nvidia-glx-new, nvidia-glx and nvidia-glx-legacy. From reading the descriptions, nvidia-glx is the driver needed for a GeForce 4 card. Do I need to do anything else besides just check the driver for installation and apply? Because that's what I've done and nothing has happened.

Thanks for the help :)

---

### Post by xc3RnbFO8P on 2008-08-03
I am not sure, but I think you need **nvidia-glx-legacy**

---

### Post by drewcoon on 2008-08-04
What else do I have to do besides check the package and install it? I've only ever successfully installed one other driver for a 8600 GT with the installer from nVidia's site, so I'm not sure how to do it from package manager.

---

### Post by redpotatoes on 2008-08-04
Here's what I've done on my NVidia Geforce TI-4200:

```
sudo apt-get install nvidia-glx

```

and once the installation complete run:
```
sudo nvidia-glx-config enable
```

Worked for me.

---

### Post by drewcoon on 2008-08-16
> **redpotatoes said:**
> Here's what I've done on my NVidia Geforce TI-4200:

```
sudo apt-get install nvidia-glx

```

and once the installation complete run:
```
sudo nvidia-glx-config enable
```

Worked for me.

I get a command not found when I try running nvidia-glx-config... I do have an nvidia-config program though, but it doesn't take the 'enable' parameter.

I've still had no progress with this problem and it's starting to feel sort of hopeless getting it to work... Does anyone else have any advice?

---

### Post by benerivo on 2008-08-16
You could try editing your xorg.conf to ensure that the driver is listed as nvidia in 'Section "Device"', and the various 'composite' options are included in 'Section "Screen"' so that the desktop effects can be enabled.```
sudo nano /etc/X11/xorg.conf
```Here is mine```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Option		"RenderAccel" "True"
	Option		"AddARGBGLXVisuals"  "True"
	Option		"DamageEvents" "True"
	Option		"UseEvents" "False"
	Option		"TripleBuffer" "True"
	Option		"BackingStore" "True"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
```

---

