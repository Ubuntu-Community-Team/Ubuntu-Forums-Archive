---
title: "NVIDIA MX 440 3D Lockup"
date: 2008-07-17
forum: Multimedia Software
---

### Post by sjbaugh on 2008-07-17
Being new to Ubuntu, I have installed Hardy Heron on an old system with an NVIDIA MX 440 card in an AGP 4X slot.

When installing the distro there was a lot of flickering on the display. At the end of the install I took the option to install the "nvidia" Restricted driver. This has curred the flickering but now I get random lockups. I think this is when it is displaying 3D content. I have edited xorg.conf and added the following (as suggested in another thread for a different NVIDIA card):
	Option		"RenderAccel"	"Off"
	Option		"NoRenderExtension"	"Off"
	Option		"AllowGLXWithComposite"	"Off"
It has not locked up (yet!) with this setting but I get no 3D.

Does anybody have any ideas of any other changes I can make that will retain some 3D features?

Thanks, Steve, Bracknell, England.

---

### Post by wolfen69 on 2008-07-17
try removing the video driver, and:```
sudo apt-get install nvidia-glx-legacy
``` this driver would be more appropriate for that card.

---

### Post by sjbaugh on 2008-07-17
wolfen,

Thanks for that but I am not sure the safest way to remove the old driver.

Steve

---

### Post by sjbaugh on 2008-07-17
I worked out how to disable the nvidia-glx driver using:
System>Administration>Hardware Drivers
I installed the nvidia-glx-legacy driver as above and re-booted.
The driver ran OK but now I am limited to 800X600 (it was 1280X1024) and
still no 3D.

I have returned to the settings in the first post for now as at least I get the higher screen resolution.

Steve

---

