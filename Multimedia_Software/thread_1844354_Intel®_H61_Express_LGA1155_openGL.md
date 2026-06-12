---
title: "Intel® H61 Express LGA1155 openGL"
date: 2011-09-15
forum: Multimedia Software
---

### Post by konts_A on 2011-09-15
Ubuntu version 11.04

where to get drivers for chipset Intel® H61 Express LGA1155?
downloadcenter.intel.com - only windows.

**compiz --replace **
[COLOR="Red"]Compiz (opengl) - Fatal: glXCreateContext failed[/COLOR]

---

### Post by BicyclerBoy on 2011-09-15
The kernel contains support for the chipset & kernel space module for this h/w.

The video drivers are available in ubuntu repositories..
They actually come from here:
[http://intellinuxgraphics.org](http://intellinuxgraphics.org)
There are pre-compiled/packaged versions in launchpad ppa.

A bit bleeding edge maybe but xorg-edgers ppa is recommended.
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty)
There is a note about SandyBridge being disabled due to problems..

You are using core (i3 i5 i7 pre SB) intel graphics ?

---

### Post by konts_A on 2011-09-16
> 
You are using core (i3 i5 i7 pre SB) intel graphics ?

**Pentium G850**

I install 
sudo apt-get install mesa-utils
sudo apt-get install libglu1-mesa-dev freeglut3-dev mesa-common-dev
LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace 

not work

when I try
sudo apt-get remove libglu1-mesa-dev freeglut3-dev mesa-common-dev
sudo add-apt-repository ppa:cardapio-team/unstable && sudo apt-get update
sudo apt-get install cardapio-gnomepanel

Not work.

---

### Post by BicyclerBoy on 2011-09-16
LGA1155 H61 is SandyBridge..

Like I previous noted..sandybridge has been disabled in xorg-edgers due to complaints..
You may be able to reverse that.
The later kernels maybe required.

The ppa you posted is just decoration not GL/GLX driver.

---

### Post by konts_A on 2011-09-16
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo upt -getutdate
sudo apt-get install --reinstall xserver-xorg-video-intel  libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

**glxinfo | grep dire**
Xlib:  extension "GLX" missing on display ":0.0".
[COLOR="Red"]Error: couldn't find RGB GLX visual or fbconfig[/COLOR]

**glxinfo**
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

** compiz --replace**
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXCreateContext failed
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Error: initScreen failed
Compiz (core) - Error: Couldn't activate plugin 'opengl'

---

### Post by konts_A on 2011-09-16
gksudo gedit /etc/X11/xorg.conf

> Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

[COLOR="Red"]Error: couldn't find RGB GLX visual or fbconfig[/COLOR]

---

### Post by BicyclerBoy on 2011-09-16
I believe if you use the xorg.conf file, you have to have the keywords
driver "intel"

in the Device section..

Then restart gdm & check out the /var/log/Xorg.0.log

---

### Post by konts_A on 2011-09-18
> **BicyclerBoy said:**
> 
driver "intel"


I found in Xorg.0.log
[    18.920] (EE) Failed to initialize GLX extension([COLOR="red"]Compatible NVIDIA X driver not found[/COLOR])

sudo apt-get autoremove --purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

**glxinfo**
```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.12-devel
OpenGL shading language version string: 1.20
```

Thanks for your help in setting up.

---

### Post by BicyclerBoy on 2011-09-19
Good for you.
That looks okay now..

Where did the nVidia driver stuff spring from ?
Do you have optimus graphics setup or another GPU ?

---

### Post by konts_A on 2011-09-26
> **BicyclerBoy said:**
> 
Where did the nVidia driver stuff spring from ?
Do you have optimus graphics setup or another GPU ?

I changed my PC, replaced the hard drive from the old machine.
There's just something that the motherboard.

---

### Post by rodrigoclira on 2011-10-05
konts_A what's kernel version u use?

thanks

---

