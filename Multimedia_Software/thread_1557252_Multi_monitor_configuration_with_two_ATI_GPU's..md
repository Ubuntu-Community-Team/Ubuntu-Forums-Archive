---
title: "Multi monitor configuration with two ATI GPU's."
date: 2010-08-20
forum: Multimedia Software
---

### Post by xelasha on 2010-08-20
I have 2 GPUs in my system, a HD4870 and a HD4350. The HD4870 has a Benq 24" and a Dell 17" which are working fine in a multi-display desktop setting (No Xinerama) configured via CCC. 

On the HD4350 I have a single Samsung 17" which in CCC is listed as '[Unknown Display] Unknown adapter' and cannot be used. How can I get that working properly so I can configure it as an additional screen in this setup?

Here is some information to help solve the problem.
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3200 3200
		Depth     24
	EndSubSection
EndSection

```

HD4870
```
description: VGA compatible controller
                product: RV770 [Radeon HD 4870]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:32 memory:c0000000-cfffffff(prefetchable) memory:e7000000-e700ffff ioport:9000(size=256) memory:e6000000-e601ffff(prefetchable)
```

HD4350
```
     description: VGA compatible controller
                product: RV710 [Radeon HD 4350]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:16 memory:d0000000-dfffffff(prefetchable) memory:e5000000-e500ffff ioport:a000(size=256) memory:e4000000-e401ffff(prefetchable)
```

Hope you guys can help me out, I have tried a few different configurations in Xorg but I don't have a great understanding of the configuration files so I have broken it a few times.

I have read through this guide [http://mugginix.com/articles/2009/Nov/12/Xinerama_Composite_Fail/](http://mugginix.com/articles/2009/Nov/12/Xinerama_Composite_Fail/)
It's a guide based on the work around for multiple Nvidia GPUs with a six monitor configuration while still being able to run visual effects without a hitch. But I didn't continue after reading "If you're prepared to use ATI cards, and therefore deal with their drivers, a better option might be to buy an Eyefinity card."

Since that is based on the drivers back then I figure maybe it's possible with ATI drivers now, but I'm going to need a fair bit of help so please if any of you have any ideas or suggestions I would be very appreciative. I'm sticking to Ubuntu this time around there is no doubt there so I would really like to get my third monitor working.

---

### Post by xelasha on 2010-08-22
*bump*

---

### Post by alfalfa31 on 2010-09-02
I'm going to make an attempt to solve this.  Give me until this weekend...

---

