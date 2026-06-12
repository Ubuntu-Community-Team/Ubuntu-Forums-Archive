---
title: "Dual monitor issue on radeon 5870"
date: 2011-02-06
forum: Multimedia Software
---

### Post by gulafaran on 2011-02-06
im using dual monitors on kubuntu 10.10 with catalyst 11.1 and everytime i close a wine game and sometimes native games the second monitor shutsdown and i have to restart the computer to get it back on so i would appreciate any tips on perhaps fix this and im not seeing any errors or warnings in xorg log file

dmesg | grep fglrx

```
4.839347] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    4.900502] [fglrx] Maximum main memory to use for locked dma buffers: 7766 MBytes.
[    4.900551] [fglrx]   vendor: 1002 device: 6898 count: 1
[    4.900826] [fglrx] ioport: bar 4, base 0xee00, size: 0x100
[    4.901092] [fglrx] Kernel PAT support is enabled
[    4.901105] [fglrx] module loaded - fglrx 8.81.5 [Jan  4 2011] with 1 minors
[    6.263329] fglrx_pci 0000:01:00.0: irq 47 for MSI/MSI-X
[    6.263761] [fglrx] Firegl kernel thread PID: 1293
[    6.263964] [fglrx] IRQ 47 Enabled
[    6.429615] [fglrx] Gart USWC size:1280 M.
[    6.429617] [fglrx] Gart cacheable size:508 M.
[    6.429620] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[    6.429622] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
[    6.429624] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[  975.601943] [fglrx] IRQ 47 Disabled
[  976.037085] fglrx_pci 0000:01:00.0: irq 47 for MSI/MSI-X
[  976.037530] [fglrx] Firegl kernel thread PID: 3023
[  976.037698] [fglrx] IRQ 47 Enabled
[  976.192276] [fglrx] Gart USWC size:1280 M.
[  976.192278] [fglrx] Gart cacheable size:508 M.
[  976.192281] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  976.192283] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
[  976.192284] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000
```


fglrxinfo

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series
OpenGL version string: 4.1.10428 Compatibility Profile Context
```

and the xorg.conf 

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
        Load  "extmod"
        Load  "dbe"
        Load  "xtrap"
        Load  "record"
        Load  "dri"
        Load  "glx"
        Load  "GLcore"
        Load  "freetype"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
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
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	Option	    "Monitor-CRT2" "0-CRT2"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3600 1920
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection


```

---

