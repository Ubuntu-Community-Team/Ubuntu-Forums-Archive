---
title: "Stuck at 640X480 NV18 AGP Chipset"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by ubu_n00b69 on 2006-10-22
I have been stuck on 640X480 Res since I Installed last night.

Here is my config file. I must be missing something and just can't see it.
The ONLY resolution available is 640X480 when I go to change it, but, the config file shows the monitor, all of the supported resolutions, the Video Chipset (NV 18, Ge Force4 MX)

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-96
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


I am stumped, not that it would take much for that!!!

This is my first run at a Linux distro, and it seems it will be really nice once I get the hang of the Linux way of doing things. 
I have held BG's hand for too long, and it's showing :-)

Thanks for any help that is offered...It is truly appreciated.

---

### Post by teet on 2006-10-22
Since you have an nvidia card...

Try installing the nvidia drivers.

Open up synaptic and search for "nvidia".  You'll want to install something called "nvidia-glx" if my memory serves me correctly.

-teet

---

### Post by tseliot on 2006-10-22
Install the Nvidia driver by following Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

and if that doesn't solve the problem try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

