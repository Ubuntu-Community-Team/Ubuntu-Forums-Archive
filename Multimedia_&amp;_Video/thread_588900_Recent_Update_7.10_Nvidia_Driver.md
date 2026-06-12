---
title: "Recent Update 7.10 Nvidia Driver"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by kaoskorruption on 2007-10-23
Hey,

I recently upgraded my system which has an nVidia GeForce FX 5200 graphics card, and I enabled the "NVIDIA accelerated graphics card driver" (nvidia-glx). This requires a reboot, so I did, but when it loaded back up, as soon as it finished loading Ubuntu and would normally get to the login screen, the screen just went blank as if it was not even getting a signal.

If anybody can offer a suggestion of how to fix this I would greatly appreciate it.

Thanks

---

### Post by akshayas1986 on 2007-11-02
Hey
I have the same problem too.

---

### Post by staticsage on 2007-11-02
To switch back to the default driver, choose fail safe mode from grub. This will boot you in to a terminal.

After logging in, type

```
sudo nano /etc/X11/xorg.conf
```

Scroll down until you see something similar to this:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection
```

Change "nvidia" to "nv" and save the file.

You can now reboot or type ```
sudo /etc/init.d/gdm restart
```

Hopefully you will boot into gnome. Post back if you need any more help or run into problems.

---

### Post by akshayas1986 on 2007-11-02
Hey
Staticsage, thanks for replying.

Actually I had created a backup of my xorg.conf file and so fortunately I just renamed it as xorg.conf and started xorg working.

---

### Post by eye208 on 2007-11-02
> **kaoskorruption said:**
> If anybody can offer a suggestion of how to fix this I would greatly appreciate it.
Please take a look at the "Modes" line in the xorg.conf file. Are all the modes listed there supported by your display?

For example, if you have a 15inch TFT display and the Modes line contains 1280x1024 (typical 17inch resolution), some drivers (such as the VESA driver) will automatically use a lower resolution (if the monitor is [DDC](http://en.wikipedia.org/wiki/Display_Data_Channel)-capable), but the Nvidia driver will not. This might result in a blank screen or an "out of range" warning message, depending on the type of monitor. The Nvidia driver will always use the highest resolution specified in the Modes line of xorg.conf by default, no matter if the display can actually handle it. So you have to check and adjust this line prior to activating the Nvidia driver. You can do this either by editing the file by hand or by running "sudo dpkg-reconfigure -pmedium xserver-xorg" and selecting manual monitor configuration.

---

