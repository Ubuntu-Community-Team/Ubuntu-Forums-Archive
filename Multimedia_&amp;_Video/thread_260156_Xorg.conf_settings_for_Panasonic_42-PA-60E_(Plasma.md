---
title: "Xorg.conf settings for Panasonic 42-PA-60E (Plasma)?"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by ubu-for on 2006-09-18
Does anybody know the Xorg.conf settings for a Panasonic 42-PA-60E to watch DVDs in correct aspect ratio?

My old settings for a 4:3 TV:
Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
	Option          "TVOutFormat" "COMPOSITE" #or "S-VIDEO" etc 
   	Option          "TVStandard" "PAL-G" #or NTSC, PAL-B etc 
   	Option          "ConnectedMonitor" "TV" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection
...
Section "Monitor" 
	Identifier	"TV" 
	HorizSync	60
	VertRefresh	56-76 
EndSection
...
Section "Screen" 
	Device		"Device[1]" 
	Identifier	"Screen[1]" 
	Monitor		"TV" 
	DefaultDepth	24 
	SubSection "Display" 
		Depth 24 
		Modes "800x600" 
	EndSubSection    
EndSection

THX!

---

