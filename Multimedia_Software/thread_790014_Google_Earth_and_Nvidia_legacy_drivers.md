---
title: "Google Earth and Nvidia legacy drivers"
date: 2008-05-11
forum: Multimedia Software
---

### Post by nemarona on 2008-05-11
I can't get Google Earth to work on my pc.

If I use only open-source video drivers, then GE just crashes at startup and logs me out from Ubuntu.

I installed the nvidia-glx-legacy package and activated it through Xubuntu's "Hardware Drivers". When I run GE now, it complains it cannot identify my graphics card, and doesn't work.

My graphics card is listed by lshw as
```
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 15
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
```

Some relevant sections from my xorg.conf file:
```
Section "Monitor"
        Identifier   "Configured Monitor"
        VendorName   "Samsung"
        ModelName    "SyncMaster 551v"
	DisplaySize  267 200
        HorizSync    30-55
        VertRefresh  50-120
	Option       "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection "Display"
                Modes     "1024x768"
        EndSubSection
EndSection
```

Thanks in advance for any help with this!

---

