---
title: "Resolution not available for all users"
date: 2011-08-24
forum: Multimedia Software
---

### Post by kyutums on 2011-08-24
I am using Ubuntu 11.04 on an Intel D510MO motherboard as a low-end surfing computer. The monitor, a Viewsonic VA1926w, has a maximum resolution of 1440x900.

Before, I was only able to get 1280x720 so I had to create an xorg.conf and edit it manually. "X -configure" gave an error (Number of created screens does not match number of detected devices. Configuration failed. ddxSigGiveUp: Closing log) so I had to copy the created file to /etc/X11/xorg.conf manually and placed the following in xorg.conf:
```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Unknown"
	ModelName    "ViewSonic VA1926w"
	HorizSync    24.0 - 82.0
	VertRefresh  50.0 - 75.0
	Option       "DPMS"
EndSection
```
```
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 24
	Option "TwinView" "0"
	Option "metamodes" "1440x900 +0 +0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection
```
(taken from [http://ubuntuforums.org/showthread.php?t=1488888](http://ubuntuforums.org/showthread.php?t=1488888))

Although I now have 1440x900 on the main user (the sudo user), other users on the computer just get 1280x720. The maximum resolution of their monitor is just 1280x720.

Any idea on how I can make 1440x900 available on all users?

---

