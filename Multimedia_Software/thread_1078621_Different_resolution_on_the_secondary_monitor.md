---
title: "Different resolution on the secondary monitor"
date: 2009-02-23
forum: Multimedia Software
---

### Post by alex_sv on 2009-02-23
hi.
is it possible to have different resolutions on Laptop display and Secondary Monitor?
I configured my laptop to have secondary monitor via ATI Catalyst Control Center, but either laptop display and monitor have the same resolution: 1280x800. Monitor is designed to have 1280x1024 resolution, so it's performance is shaky and messy in case of any resolution with 16:9 aspect ratio.
I tried to configure monitor manually via xorg.conf, but I wasn't succeed.
All I want to do is to configure laptop display to be 1280x800 and secondary monitor - 1280x1024.
I have read manuals dedicated to X server and particulary to xorg.conf magic, but I still have no working version, I just ran out of any ideas.
Please, help me.

At the moment I have the following xorg.conf file:

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30.0 - 81.0
	VertRefresh	56.0 - 76.0
EndSection

Section "Screen"
	Identifier	"Configured Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection 	"Display"
		Depth	24
		Modes	"1280x800@60"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

My monitor is Samsung SyncMaster 960bg.

---

