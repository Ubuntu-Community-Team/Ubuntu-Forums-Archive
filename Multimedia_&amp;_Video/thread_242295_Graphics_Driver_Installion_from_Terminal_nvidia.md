---
title: "Graphics Driver Installion from Terminal nvidia"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by larrybrazos on 2006-08-23
i have installed linux server edition because i want to learn LAMP, but i also want GUI.  so i did apt-get install update, apt-get install ubuntu-desktop and everything went fine, but i have nvidia evga 7800gt card and everything is scrambled.  now, is there a way to download and istall nvidia drivers from a command line only - for example boot to LAMP server recovery mode and perform the driver installation from command line.  i tried using my ubuntu desktop edition disck to boot to safe mode and do all the updating from that, but i couldmn't figure out how to get into my lamp server file system from live cd.

. . . or should i install dekstop edition and just grab everything i need for learning lamp.

thanks.

---

### Post by spockrock on 2006-08-23
ok I have the same problem when I installed ubuntu on my bfg 7800gt.  you get to gdm and then after login the graphics just poop out.

ok boot, once you get to gdm press ctrl+alt+F1

you should get to virtual terminal, black screen with white text.  Login.

I am assuming you have enabled the extra repositories, if you might not need to or you will find out after this.

```
sudo apt-get install nvidia-glx
```

ok now that you have that downloaded and installed, the next step is to enable the settings automagically, however I find that it never does. so the manual way it is...first back up xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

now we enable the driver.

```
sudo nano /etc/X11/xorg.conf
```

now scrolldown to this bit in the xorg.conf

```

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Screen      	0  
    	Option     	"TwinView"	"true"
    	Option     	"MetaModes"	"1600x1200,1600x1200"
    	Option     	"TwinViewOrientation"	"RightOf"
    	Option     	"SecondMonitorHorizSync"	"50-75"
    	Option     	"SecondMonitorVertRefresh"	"60-80"
	Option		"RenderAccel"			"true"
	Option		"NoLogo"	"True"
	#Option 		"AllowGLXWithComposite"	"true" 
EndSection

```

the important part is that Driver line, yours should read 
```
Driver   "nv"
```

change it to 
```
Driver   "nvidia"
```

just change that and you will have nvidia drivers....enjoy.

---

### Post by larrybrazos on 2006-08-23
frist off, thanks for the help. i figured this would be a common problem, but this is how far i got . . .


did sudo apt-get install nvidia-glx
then sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
then sudo nano /etc/X11/xorg.conf

all went smoothly.

changed the file to read . . .
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Screen      	0  

Left the options out so i didn't complicate things.

Result - failed to start xserver

Am I missing something?  Thanks again.

---

### Post by spockrock on 2006-08-23
```
nvidia-glx-config enable
```

this is the automagic command that should enable it by changing nv to nvidia.

however, that should of worked.  you didn't update anything else did you??

---

### Post by spockrock on 2006-08-23
oh also did you change the Identifier and Bus ID lines, plx tell me you didnt.  if so you need to change them back, just look at the back file you made and fix the changes if you did, you were only suppossed to change teh driver line.  I am sorry I should of made that clear.  if you did then just do this to fix your mistake.

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
sudo nano /etc/X11/xorg.conf

```

and just change the nv to nvidia.

also if that isnt it maybe it didnt install the restricted modules, (its done it for my automagically, but this is how your would do it.

```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

---

### Post by larrybrazos on 2006-08-24
ok, decided to wipe the server installation and install desktop edition.  followed your steps after the reinstall and everything went smoothly.  thanks.

---

