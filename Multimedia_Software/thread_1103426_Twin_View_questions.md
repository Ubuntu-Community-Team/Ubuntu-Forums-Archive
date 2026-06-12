---
title: "Twin View questions"
date: 2009-03-22
forum: Multimedia Software
---

### Post by womblet on 2009-03-22
Hi. I am trying to figure out how to have my desktop extend over two screens. Currently, it is cloned on both screens.

I typed gksudo gedit /etc/X11/xorg.conf and added all the lines starting with "Option". All of the help examples I saw showed a BUS ID which I couldn't see in my xorg.conf file.

 > Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	Option "UseDisplayDevice" "string" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection

Thanks for your help.

---

### Post by Yerknutz on 2009-03-23
If you are running an Nvidia or ATI card I would recommend installing Envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)). This will help install the best/latest driver for your video card and also installs the Nvidia X Server Settings GUI interface in your System/Administration.

If that doesn't do everything you need the section of my xorg.conf that I use beautifully with 2 Dell 20" LCDs side by side looks like:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1680x1050 +0+0, DFP-1: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by womblet on 2009-03-23
Thanks Yerknutz. 
I installed Envy, and not much appeared to happen after I ran it to update the drivers. 
I tried changing the xorg.conf file, but managed to mess it up so now when my computer boots I get a crazy unreadable screen. I saved the part of xorg file as backup that I changed, but how do I navigate into the file to change it?

---

### Post by Yerknutz on 2009-03-25
Before I started using Envy and Nvidia X Server Settings interface and I messed up my xorg.conf I would boot to the Ubuntu live cd and then use terminal to sudo gedit my xorg.conf.

When you had Envy installed did you use Nvidia X Server settings or try to edit your xorg.conf manually? Once I had that installed I have had to manually edit xorg.conf anymore. I make all my settings changes in the NVidia GUI.

---

### Post by norwoods on 2009-03-25
use System-->Administration-->Synaptic Package Manager to install nvidia-settings
you get a command line by starting Applications-->Accessories-->Terminal
you get admin privileges by starting a program gksu for gnome programs so type:
gksu nvidia-settings
when the nvidia gui interface is running, click X Server Display Configuration. 
click Configure...
click the TwinView radio button
click OK
set up anything you want
click Save to X Configuration File
click Quit

i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

