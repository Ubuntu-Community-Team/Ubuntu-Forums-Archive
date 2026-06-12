---
title: "[SOLVED] After temporarily disabling nvidia driver, cannot re-enable it!"
date: 2008-10-07
forum: Multimedia Software
---

### Post by matthewbpt on 2008-10-07
Hey everyone,
I have a very strange problem which i really need to fix. I've been having trouble getting my laptop to suspend, and I read somewhere that the nVidia driver can affect suspend, so I thought I'd try out suspending with the driver disabled. I open up the Proprietary Hardware drivers window from System > Administration and un-tick the nVidia Driver then I restart. Ubuntu boots in low graphics mode (with 800x600 resolution instead of 1440x900, and I can't change the resolution)! So I think obviously this isn't what I want and I re-enable the driver and reboot ... my laptop still boots in low graphics mode! So I run the command 'sudo dpkg-reconfigure -phigh xserver-xorg' and reboot. The laptop boots up fine, with the correct resolution etc, BUT its running in 2D mode, the nVidia driver is still not enabled. So enable it and reboot ... again low graphics mode, but the driver manager says the driver is installed and in use. Help! I need my laptop to run in 3d mode, not just so I can get nice desktop effects, but also so I can run Matlab which I need for my physics course, and which requires openGL. The funny thing is that it was working absolutely fine with the driver before I disabled it and re-enabled it. So at the moment I can only run in 2D acceleration mode with full resolution, or with the NVidia driver enabled and in low graphics mode with terrible resolution.

My graphics card is Geforce Go 7600
this is my x.org file (in high resolution 2D mode which I'm in right now)

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Help me please!
-Matt

PS. The irony is that disabling the driver didn't even solve my suspend problem lol

---

### Post by justsomedude on 2008-10-07
I'd try nvidia-xconfig.

Just in case, backup your xorg.conf first:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then, do:
```

sudo nvidia-xconfig 
```

and restart X.

---

### Post by matthewbpt on 2008-10-07
I tried this, didn't have any effect whatsoever I'm afraid. And when I open nvidia-settings after enabling the driver and rebooting, it says that I'm not using the nvidia driver, but the Hardware drivers says it is enabled and in use!

---

### Post by Bucky Ball on 2008-10-07
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
```That is my xorg.conf with the nvidia driver. Strange problem. All I can suggest is disabling the driver again and making sure it is completely unticked and not in use, logout then back in ... Then try again. :)

Have you downloaded nvidia-settings, BTW? Do you have the Nvidia X server settings under System->Admin?

---

### Post by matthewbpt on 2008-10-07
Did that a million times lol and it didn't make a difference. But I've now solved the problem by using EnvyNG instead to install the driver which worked perfectly, it's very strange though that the normal method which worked fine for me before suddenly stopped working. =s oh well at least it works now!

---

