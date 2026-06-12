---
title: "Adding screen resolutions"
date: 2006-08-24
forum: Multimedia &amp; Video
---

### Post by neonhomer on 2006-08-24
OKay, I am a newbie to Linux. When I initially setup Ubuntu, I only set it for three resolutions, 640x480, 800x600, and 1024x768. Now that I am using it, I need a higher resolution.... How do I add another resolution.

I tried editing the xorg.conf file, but it wont let me save it because I am not the root user. To top it off, I cant log in as root to edit it!

There has to be something I am missing here....

I am running a Dell Inspiron 5000e, P3-600, and ATI Rage Mobility 3D video (According to the device manager in Ubuntu.. or is it Gnome?)

---

### Post by TrendyDark on 2006-08-24
```
sudo dpkg-reconfigure xserver-xorg
```

Do that in the terminal and you should be able to add more resolutions.

If you just want to edit the xorg file, you'll need to use SUDO to act as root.

i'm not sure where the xorg configuration file is located, so this is just an example, but here's how you do it:

```
sudo gedit /path/to/xorg.conf
```

using sudo, you'll be asked to enter a password, this is the root password and is how you should always do something as root. The password is the same password you use to login under your account.

Hope that helps :D

---

### Post by thewayofzen on 2006-08-24
First thing i would suggest doing is backing up your original xorg.conf file.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak

Then if you wish to manually edit the file to add your monitors sync rates or  new resolutions..

Assuming you do have gedit..

sudo gedit /etc/X11/xorg.conf   

if not try this in terminal

sudo nano /etc/X11/xorg.conf

---

### Post by neonhomer on 2006-08-24
Okay, I tried the reconfig, and selected the extra resolutions, but it did not add them to the Screen Resolution settings. I did reboot after the reconfig, and nothing..

I also tried adding the resolution manually to the xorg.conf file, and that did nothing either....

This could be a plus... this is the first time today I have fired up my windows Laptop... been using the ubuntu laptop all day! (granted all I did was email and internet)

---

### Post by crispy_420 on 2006-08-25
What does your monitor support?

to edit your xorg.conf:

> sudo gedit /etc/X11/xorg.conf

add in your resolutions 

if you mess up and you can't get gui after reboot and stuck and command line

> sudo nano /etc/X11/xorg.conf

save file (control + x -> y -> enter

to get gui: startx

---

### Post by neonhomer on 2006-08-25
I added the next resolution up 1152x864, which I believe the display would support. However, it doesnt even show up in the list to select from when I restart....

---

### Post by neonhomer on 2006-08-26
Quick edit... the video is a Rage Mobility M3. 

The display (the LCD) has supported up to 1152x864 under Windows....

This is part of the xorg.conf file.... with the added 1152x864 resolution added...


Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by apc15x on 2006-08-27
I am also a newbe and when I installed Linus it did not ask me about screen resolutions, it just installed. Now the screen res is at the maximun of 1600x1200 at 76hz. I want to go down to 1024 x768 but when I try to change it in screen resolution it just reboots at the default of 1600x1200. Can anyone help me?  Thanks in advance.

apc15x

---

