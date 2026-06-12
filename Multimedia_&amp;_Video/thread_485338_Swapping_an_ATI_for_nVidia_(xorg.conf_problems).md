---
title: "Swapping an ATI for nVidia (xorg.conf problems)"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by CityofAsh on 2007-06-26
I recieved my new Nvidia geforece FX5200 Vid card today. I wanted to replace the ATI Radeon 9200 as it unsupported by feisty. As of now i am running Edgy 6.10.

I replaced the ATI vid card and on boot up hang. Then was forced to restore my xorg.conf

```
dpkg -reconfigure -phigh xerver-xorg
```
Ran this and was able to select NV for the driver.

Now my xorg.conf file is running default settings. 

How can i get the Nvidia drivers to be recognized by xorg.conf?
Xorg.conf reads as follows.

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60

```

My display looks really crappy.

Any suggestions?

---

### Post by SneakyMonkey on 2007-06-26
Here is a great HOWTO for many different versions of Ubuntu.

[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

I hope you can get your drivers working.

---

