---
title: "please help Nvidia gforce fx 5500"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by nal on 2005-10-18
I tried doing the apt-get install nvida stuff i saw under nvida sucsess stories and when i rebooted ubuntu showed the load up screen then froze on a black screen and stayed there locked.  can some one give me a step by step on how to install the new nvida drivers? I still quite new to linux and just need that and cedega to work  bought cedega last night but still can use it right.  But mainly i need a step by step on doing the graphics card no need to waste yall time on cedegea :P ill figure tht out in sooner,,,,most likly later :P

---

### Post by vega113 on 2005-11-27
got the same problem. up!

---

### Post by greenwom on 2005-12-29
I just did it.


I pluged the card in, booted up 
X failed then the system goes to command line.
You need to know the cards BusID so run

```
 sudo X :1 -scanpci
```  

Look for this line ```
(2:11:0) unknown chip (DeviceId 0x0326) from nVidia Corporation

```

back up and then edit your /etc/X11/xorg.conf

change your card info to this
```
Section "Device"
	Identifier	"NVIDIA GeForce FX5500"
	Driver		"nvidia"
	BusID		"PCI:2:11:0"
#	Option		"UseFBDev"		"true"  ##don't know if you need this
EndSection
```
You will also have to change the device name towards the end of the xorg.conf file.  Look at the 'device' by the screen resolution options.
Also if you try 'startx' it'll show you what else is jacked (by line number)

Then do this
```
apt-get install nvidia-glx
apt-get install nvidia-settings
```

Then 
```
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```
Then add this (it's a new file so it will be lank)
Insert the following lines into the new file
```

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

```
Then reboot

Also look at [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

Hope this works for you, post problems.
(man this post almost makes it sound like I know what I'm doing)  :rolleyes:

---

### Post by vega113 on 2005-12-30
thanks

---

### Post by kybishop on 2006-02-12
umm, yeah same problem but . . .

i can't use gedit, when i try to, it says ```
gtk-warning **: cannot open display:
```

im pretty new to linux, so whats the command to open a non graphical editor to /etc/X11/xorg.conf

---

