---
title: "ati cataclyst 10.10 driver"
date: 2010-11-18
forum: Multimedia Software
---

### Post by kartabosh on 2010-11-18
can anyone tell me a way to figure out if i installed the drivers correctly?
if i run fgrlxinfo i get 
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 3.3.10057 Compatibility Profile Context

```
my xorg.conf contains
```
[...]
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection
[...]
```

does that mean that drivers are up and running?

because i get display glitches, the kind you get in windows when the drivers are not installed properly
i only noticed them in thunderbird
i get a gray area which only goes away if i hover the cursor over it
here's a picture
anyone?
[http://imm.io/media/27/27O5.jpg](http://imm.io/media/27/27O5.jpg)

---

### Post by Saner on 2010-11-18
Looks like it working (well as working as fglrx gets) 

10.11 came yesterday - [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

---

