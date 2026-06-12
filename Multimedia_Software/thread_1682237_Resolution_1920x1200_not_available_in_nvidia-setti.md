---
title: "Resolution 1920x1200 not available in nvidia-settings"
date: 2011-02-05
forum: Multimedia Software
---

### Post by smartbei on 2011-02-05
I just bought a new 24inch monitor that supports the resolution 1920x1200. Unfortunately, the nvidia-settings dialog does not have this resolution as an option (currently running on 1920x1080). The graphics card is Geforce 6200 (should support the wanted resolution), and the monitor is connected with the VGA cable (if that matters).

How do I add this option?

Thanks!

---

### Post by johntaylor1887 on 2011-02-05
Are you opening nvidia-settings with:
```
gksudo nvidia-settings
```??????
You must do that to make changes.

---

### Post by smartbei on 2011-02-05
Yes, I have tried that - 1920x1200 is not available in the resolution drop-down box. How do I add it as an option? Is there another way to set the resolution?

---

### Post by johntaylor1887 on 2011-02-05
Which driver did you use?

---

### Post by BicyclerBoy on 2011-02-05
All the cheap TV display 16:9 monitors are 1920x1080 native.
The expensive 16:10 computer monitors from Dell iApple & LG245 etc are native 1920x1200.

Your monitor can have a input video mode capability that exceeds its native resolution; this is a function of the pre-scaler.

The VGA connection, in new HDMI monitors, can limit the options to standard video modes & 60Hz only modes.

Your /var/log/Xorg.0.log  will list the EDID modes read from the display...

---

### Post by smartbei on 2011-02-05
The monitor is a relatively expensive Dell U2410. I bought it partly because it is native 1920x1200.

These look like the only lines relevant from /var/log/Xorg.0.log: 
```

[   998.316] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select@1920x1200+0+0"
[  1010.455] (II) NVIDIA(0): Setting mode "CRT-0:1920x1080@1920x1200+0+0"
[  5727.079] (II) NVIDIA(0): Setting mode "CRT-0:1920x1080@1920x1080+0+0"

```

The driver I am using is the newest one available from ubuntu (the "version current" in the Additional Drivers dialog).

---

### Post by BicyclerBoy on 2011-02-05
That almost looks like your xorg.conf file has a mode entry for 1920x1080 & the driver is then excluding the 1920x1200.

Edit/copy/delete your /etc/X11/xorg.conf file & reboot.

If you have a simple video-monitor setup, then the xorg.conf file is not needed.

---

### Post by smartbei on 2011-02-05
Ok, I tried that and it worked! Looking at the original xorg.conf, I am not quite sure what caused the problem:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```
In fact, I am unsure what created that xorg.conf file. Anyway, thanks a lot!

---

