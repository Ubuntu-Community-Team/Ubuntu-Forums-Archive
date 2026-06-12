---
title: "Alpha 2 for Natty - Screen Flashes black."
date: 2011-02-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cmh8133 on 2011-02-24
My screen flashes black for a second or two then comes back. I can type while the screen is black.

I am running 11.04 Alpha 2 (currently update/upgraded) on a GX620 here are some particulars.


lshw -class video
  *-display:0             
       description: VGA compatible controller
       product: RV380 [Radeon X600 (PCIE)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:e0000000-efffffff memory:fe9e0000-fe9effff ioport:dc00(size=256) memory:fea00000-fea1ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV380 [Radeon X600]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe9f0000-fe9fffff

Section "Device"
	Identifier	"Configured Video Device"
        Driver               "ati"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	VendorName	"Dell"
	ModelName	"2209WAF"
	Modeline "1680x1050"  187.00  1680 1800 1976 2272  1050 1053 1059 1099
	Modeline "1680x1050"  174.00  1680 1800 1976 2272  1050 1053 1059 1096
	Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089
	HorizSync	28-96
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection	"Display"
		Viewport	0 0
		Depth		24
		Modes	"1680x1050"	"1440x900"	"1360x768"	"1280x1024"
	EndSubSection
EndSection


any ideas?

[email]chouck@binghamton.edu[/email]

---

