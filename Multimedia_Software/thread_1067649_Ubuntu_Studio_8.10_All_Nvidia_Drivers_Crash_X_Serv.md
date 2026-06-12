---
title: "Ubuntu Studio 8.10 All Nvidia Drivers Crash X Server on Boot"
date: 2009-02-12
forum: Multimedia Software
---

### Post by Tindytim on 2009-02-12
I recently installed Ubuntu Studio 8.10 on a fresh Partition.

I've installed the restricted drivers in the repos, I've installed the drivers from the Nvidia site, and I can't even get the EnvyNG GUI to work. The text based core version works, but I have the same issue.

Everytime I install a driver, when I restart, there is an issue with the X server, and it refuses to start up. I then have to restart again and boot into recovery mode.

I have a 9800 GTX, here is my xorg.conf:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3200 1228
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

Help?

---

### Post by Tindytim on 2009-02-13
I attempted to tinker and see if I could get this working. X still fails, I figured I'd attach the log file.

I can't even get Blender to start correctly. Any help would be greatly appreciated.

---

### Post by blufade on 2009-02-13
i've have a similar issue on my laptop
x server works fine if i disable 3d accleration

---

