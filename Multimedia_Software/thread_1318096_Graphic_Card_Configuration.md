---
title: "Graphic Card Configuration"
date: 2009-11-07
forum: Multimedia Software
---

### Post by dox_drum on 2009-11-07
Hi people,
   At the office we have a couple of desktop machines and I've installed Ubuntu in both of them.
   Everything works, but the graphic card.
```
oscar@Mephistopheles:~$ sudo lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)
oscar@Mephistopheles:~$ 
```

[LIST]
[*]I've installed the Nvidia restricted driver, but the resolution is really poor
[*]When I go to Nvidia configuration and change to the nice resolution, if I save the changes in the xorg.conf, after restart the borders of windows don't appear and terminals and menus are just white.
[*]Try envy-gn package but got same behaviour.
[/LIST]

Does anybody get a novell idea? (I don't care if it is a manual configuration of the xorg.conf file)

btw, the nvidia package is the 96, not the new ones 177 not 180.

Thank you so much!

---

### Post by zman58 on 2009-11-07
> **dox_drum said:**
> Hi people,
   At the office we have a couple of desktop machines and I've installed Ubuntu in both of them.
   Everything works, but the graphic card.
[CODE]oscar@Mephistopheles:~$ sudo lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)
[...]behaviour.
[/LIST]

Does anybody get a novell idea? (I don't care if it is a manual configuration of the xorg.conf file)

btw, the nvidia package is the 96, not the new ones 177 not 180.

Thank you so much!

This looks like a problem I was having on an older system with the Geforce MX 440. Please refer to my Post #37 on this page. I think it will help:
http://ubuntuforums.org/showthread.php?t=1313280&page=4

---

### Post by dox_drum on 2009-11-07
> **zman58 said:**
> This looks like a problem I was having on an older system with the Geforce MX 440. Please refer to my Post #37 on this page. I think it will help:
[http://ubuntuforums.org/showthread.php?t=1313280&page=4](http://ubuntuforums.org/showthread.php?t=1313280&page=4)

Hi zman58, Do you have the Nvidia driver installed?

---

### Post by dox_drum on 2009-11-07
Hey zman!
   I  modify my xorg.config file as you suggest, and additionally installed the NVIDIA driver.
   Although I got the right resolution of the monitor, the 3D effects are not working... Have you get them work?

```
oscar@Mephistopheles:~$ cat /etc/X11/xorg.conf 

Section "Monitor"
	Identifier "SyncMaster"
	Vendorname "Samsung"
	Modelname "551v"
	HorizSync 30-97
	VertRefresh 50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor "SyncMaster"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
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

This is my xorg.conf file!

Thank you again.

---

