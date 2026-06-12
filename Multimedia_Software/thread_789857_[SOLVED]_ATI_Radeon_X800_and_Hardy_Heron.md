---
title: "[SOLVED] ATI Radeon X800 and Hardy Heron"
date: 2008-05-10
forum: Multimedia Software
---

### Post by przemeklach on 2008-05-10
Hi,

New to the forums and new to linux. I've installed Hardy Heron on my virutal machine running on Windows Vista; Sun xVM. Installation of Heron went without a problem. 

I want to change my resolution but the default driver only allows 800x600, so I assumed that I need the correct drivers for my video card. I've tried several different ways of doing this as suggested in the forums but to no avail. 

I did a clean install and followed the steps as outlined here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) for 'Instructions for Ubuntu 7.04 (Feisty) and Ubuntu 7.10 (Gutsy)'. There where no instructions for Heron so I just used the most recent. I fail when I get to the part that tells me to "Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager"" There is no Restricted Drivers Manager. 

I'm seriously at a wits end here. I come from the windows world so maybe I'm going about this the wrong way. In windows I download the driver, install it and reboot, done. Here there are various ways to do the same thing and non of them seem to work. 

Please help. Below is some information about settings on my Ubuntu install:

Command: lspci -nn | grep VGA
Output: 00:02.0 VGA compatible controller [0300]: InnoTek Systemberatung GmbH VirtualBox Graphics Adabpter [80ee:beef]

Xorg.conf
From what I understand there should be something in here about my device but there really isn't. Only thing remotely close to my video card is this:
Section "Device"
     Identifier "Configured Video Device"
EndSection

---

### Post by Yellow Pasque on 2008-05-11
> **przemeklach said:**
> I fail when I get to the part that tells me to "Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager"" There is no Restricted Drivers Manager.
In Hardy, it is named "Hardware Drivers".

---

### Post by przemeklach on 2008-05-11
I thought so but didn't want to assume. Nothing appears under Hardware drivers, so I'm assuming it didn't install.

Thanks.

---

### Post by Yellow Pasque on 2008-05-11
```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by przemeklach on 2008-05-11
No luck, still not showing up.

---

### Post by przemeklach on 2008-05-11
Things have gone from bad to terrible. 

I followed yet another set of instructions that didn't work. I did the first method as indicated at this link: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide).

All the steps went fine but when I rebooted Ubuntu told me that it could not recognize my graphics adapter. I clicked on configure and I found my monitor in the list of devices. I selected my monitor and the resolution I wanted and rebooted. Now I have three desktops, non of which I can see anything on; see attached screenshot. 

Now I'm reinstalling Ubuntu for the 5th time. Can someone please help, all I want to do is run ubuntu at a higher rez. I still don't understand why this is so difficult to do. :mad:

---

### Post by st0nedpenguin on 2008-05-11
I had to manually input my horizontal and vertical refresh for my monitor into my xorg.conf, none of the GUI tools would work even if I selected my monitor from the list.

You should be able to get the frequencies from one of the GUI tools though if you select your monitor model (No idea which I used, running Windows currently), then slap them in your xorg.conf monitor section a little something like this:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	31-100
	Vertrefresh	50-160
EndSection
```

Once that was done I was able to select my resolution and refresh rate using the default Ubuntu screen resolution app and all worked fine.

---

### Post by Yellow Pasque on 2008-05-11
You can also get mode lines from the cvt tool. (Example: 1680x1050@60Hz)
```
dan@harvest:~/Desktop$ cvt -v 1680 1050 60.0Hz
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```
Change the '_' to a '@' and paste into the monitor section.

---

### Post by przemeklach on 2008-05-11
Thank you sir that made a big difference. I still don't have all the possible resolutions that my monitor can do. Is that because of a bad setting in my xorg.conf? or is it something else?

---

### Post by Yellow Pasque on 2008-05-11
You can add more resolutions in a similar manner.

In the Screen section, you can add the resolutions too.
Here's part of my xorg.conf
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option	   	"VideoOverlay" "on"
	Option	    	"OpenGLOverlay" "off"
EndSection

Section "Monitor"
	Identifier	"VX2025wm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"VX2025wm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode 0666
EndSection
```

---

### Post by przemeklach on 2008-05-11
Hi,

I have all those different resolutions in my xorg.conf; however, they don't show up in my drop down list of possible resolutions under "Screen Resolution".

---

### Post by Yellow Pasque on 2008-05-11
Hmmm. Let's examine /var/log/Xorg.0.log and see if it recognizes them.

---

### Post by przemeklach on 2008-05-11
I'm not sure if you wanted the whole file or just the part about the resolutions. I assumed just the resolutions. Here is the text:

(II) VESA(0): Total Memory: 128 64KB banks (8192kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.00-100.00 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) VESA(0): Not using mode "800x600@75" (no mode of this name)
(II) VESA(0): Not using mode "800x600@60" (no mode of this name)
(II) VESA(0): Not using mode "800x600@72" (no mode of this name)
(II) VESA(0): Not using mode "1280x768@60" (no mode of this name)
(II) VESA(0): Not using mode "800x600@56" (no mode of this name)
(II) VESA(0): Not using mode "1280x720@60" (no mode of this name)
(II) VESA(0): Not using mode "1280x800@75" (no mode of this name)
(II) VESA(0): Not using mode "1280x768@75" (no mode of this name)
(II) VESA(0): Not using mode "1280x800@60" (no mode of this name)
(II) VESA(0): Not using mode "1440x900@75" (no mode of this name)
(II) VESA(0): Not using mode "1440x900@60" (no mode of this name)
(II) VESA(0): Not using mode "1600x1024@60" (no mode of this name)
(II) VESA(0): Not using mode "1680x1050@60" (no mode of this name)
(II) VESA(0): Not using mode "1680x1050@75" (no mode of this name)
(II) VESA(0): Not using mode "1920x1200@60" (no mode of this name)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0):  Built-in mode "1280x1024"
(**) VESA(0):  Built-in mode "1152x864"
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "320x200"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1280x1024" (11b)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1152x864" (14b)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 85Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x480" (112)

I'll attach the whole file if you need.

Thanks.

---

### Post by przemeklach on 2008-05-12
Bump :)

---

### Post by bsmith1051 on 2008-05-12
this is Hardy running INSIDE a virtual machine?  If so, then you can't directly access the real video hw, just the virtual/generic "hardware".

---

### Post by przemeklach on 2008-05-12
Yes it's running inside a virtual machine. So I guess this is the best I can do at this time?

---

### Post by bsmith1051 on 2008-05-12
> **przemeklach said:**
> Yes it's running inside a virtual machine. So I guess this is the best I can do at this time?
Until someone invents a VM that exposes the video hardware directly, which I doubt will ever happen.  (Too funny that everyone missed that critical aspect of your post.)

More important, you still need help configuring the virtual video in your Sun xVM.  I would suggest looking for a Sun.com support forum.  They're the ones who would support their virtual device driver.  Personally, I've had a lot of success using VirtualBox (which Sun just purchased) which includes a                     video-driver 'update' that provides complete control of resolution and color-depth (but no hw acceleration support... yet!)

---

### Post by przemeklach on 2008-05-13
Thanks for the info. I wasn't looking for hadware acceleration or anything like that, I just wanted a bigger resolution. I'm just glad to know that the reason things aren't working properly is because of the VM and not because of the OS running in the VM.

The way things are right now is OK. I'll definately check out the sun forums as well as virtual box.

Thanks

---

### Post by gmaniac on 2008-05-13
Installing the guest addins (when running the virtual machine from the menu) 
After the mount run the linux driver as root, reboot and voila.
Also if you have a modern cpu (with virtualisation) enable the vxt /amdv from file->preferences->advanced
 for performance

---

