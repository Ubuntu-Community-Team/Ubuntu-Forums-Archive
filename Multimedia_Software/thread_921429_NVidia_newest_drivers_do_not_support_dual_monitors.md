---
title: "NVidia newest drivers do not support dual monitors"
date: 2008-09-16
forum: Multimedia Software
---

### Post by olhat on 2008-09-16
I installed Ubuntu for a couple of days ago on a separate hard drive.  Several ill behaviors occur.  One of the worse is ignoring my second monitor.

 It says that I have the newest NVidia (en8600gt) drivers but "clone screens" do not function and any choices close to "dual monitors" or "extended desktop" or anything to those meanings do not exist in my “screen resolutions” choices.

Everything works fine in Windows and my old ATI Radeon card showed dual monitors without any problems on my deceased nowadays invisible Ubuntu/Kubuntu kombo.:(



xorg.conf:


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection


“gksu displayconfig-gtk” which seems to lead to “screen and graphics preferences” that shows that I have a plugnplay default screen and nothing else.  Adding a secondary screen is greyed out.  Graphics card  is identified as (NVIDIA GeForce 8 Series).

---

### Post by howefield on 2008-09-16
have you installed nvidia-settings ?

sudo apt-get install nvidia-settings

or install from synaptic.

---

### Post by earlycj5 on 2008-09-16
> **howefield said:**
> have you installed nvidia-settings ?

sudo apt-get install nvidia-settings

or install from synaptic.

What howefield said.

nvidia-settings makes the setup a snap.

The latest driver DOES support dual monitors.  I just installed it.  I'm using a Quadro FX3700 card with dual Dell 1908WFP monitors.

---

### Post by olhat on 2008-09-17
Solved with EnvyNG.  Thanks for participating


Here are some of the events since my first post:

My initial problems seemed to be related to my repositories being disabled by default in Ubuntu.  It was easily remedied.   But dual monitors still do not work.  


When I go to System >admin >nvidia x server settings I get the following message:

	You do not appear to be using the NVIDIA X driver. Please edit your X configuration file
	 (just run 'nvidiaxconfig' as root), and restart the X server.    ENTER OK





~$ sudo nvidia-xconfig gives me following:

	Using X configuration file: "/etc/X11/xorg.conf". 

	VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf. 
                  Device section "Configured Video Device" must have a Driver 
                  line. 

	Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup' 
	New X configuration file written to '/etc/X11/xorg.conf' 

	olhat@nyl:~$ nvidia-xconfig 

	Using X configuration file: "/etc/X11/xorg.conf". 

	ERROR: Unable to write to directory '/etc/X11'. 




When downloading and trying to install NVIDIA linux repository drivers this happens:

	~$ sh NVIDIA-Linux-x86-171.06.01-pkg1.run 

	ERROR: this .run file is intended for the 
	Linux-x86 platform, but you appear to be 
	running on Linux-x86_64.  Aborting installation. 



A new driver and a new try gives this:


	  ERROR: You appear to be running an X server; please exit X before            

	         installing.  For further details, please see the section INSTALLING   

	         THE NVIDIA DRIVER in the README available on the Linux driver         

	         download page at [www.nvidia.com](www.nvidia.com).







next thing I will try is this one

Are you trying to install a custom nvidia driver? You can get one from synaptic. To shutdown your X server, hit CTRL-ALT-F1, log in at the prompt, and typesudo /etc/init.d/gdm stopThis quits X, the basis for linux GUI's. Then run the nvidia setup program from your console. To start X (and GNOME) again, type:sudo /etc/init.d/gdm startHowever, you should be able to get the nvidia drivers from synaptic. Look for a howto in the tips and tricks section.



Lots of waste of time and irritation until I accidentally found EnvyNG that solved my problems in a snap even if I had to go the rounds there a cpl of times until the window to click my second display “enabled” mystically appeared in front of my eyes.  
:lolflag:

---

